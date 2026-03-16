---
title: Test Crash Page
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
> ❗️ SQL Server Edition and Service Pack Support
> 
> Our SQL Server Connectors and SQL Server's Change Data Capture feature are only supported on **Standard** or **Enterprise** editions running **AWS Engine Version SQL Server 2016 13.00.6300.2.v1** or newer

# Prerequisites

An RDS [master user account](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.MasterAccounts.html).

> 📘 
> 
> You **must **have master user privileges to enable CDC on an Amazon RDS SQL Server database.
> 
> After CDC is enabled, any user who is `DB_OWNER` of that database can enable or disable CDC on tables in that database.

# SQL Server Setup

## Create a role and user

> 👍 
> 
> You can create a separate user and role exclusively for Streamkap or use existing ones. When using existing, make sure to modify any Streamkap scripts as necessary.

```sql T-SQL
-- Replace {database}, {password} placeholders
-- {database}: name of the database Streamkap should capture
-- {password}: a strong password complying with your security policies
-- {schema}: name of the schema Streamkap should capture tables from
USE {database};
GO
CREATE LOGIN streamkap_user WITH PASSWORD = '{password}';
CREATE USER streamkap_user FOR LOGIN streamkap_user;

CREATE ROLE streamkap_connector;
ALTER ROLE streamkap_connector ADD MEMBER streamkap_user;

GRANT SELECT ON DATABASE::{database} TO streamkap_connector;
GRANT SELECT ON SCHEMA::{schema} TO streamkap_connector;
GO
```



> 📘 Restricting table access
> 
> If you do not want Streamkap to access all tables in the schema, remove Line 14 from the script above and add the following for every table Streamkap can access.
> 
> ```sql T-SQL
> -- Replace {schema} and {table} placeholders
> -- {schema}: name of schema Streamkap should capture
> -- {table}: name of table Streamkap should capture
> GRANT SELECT ON {schema}.{table} TO streamkap_connector;
> ```

## Enable CDC on a database

Copy paste the script below into SQL Server Management Studio or Azure Data Studio, change placeholders as required, and then run all queries.

> 👍 
> 
> If you're not sure what the `{path}` placeholder should be, we recommend using the same location as the database's primary data files. This script helps you get that.
> 
> ```sql T-SQL
> -- Replace {database} placeholder
> -- {database}: name of the database Streamkap should capture
> USE {database};
> GO
> SELECT LEFT(df.physical_name, LEN(df.physical_name)-CHARINDEX('\', REVERSE(df.physical_name))) AS file_path
> FROM sys.database_files AS df
> INNER JOIN sys.filegroups AS fg
> ON df.data_space_id = fg.data_space_id
> WHERE fg.name = N'PRIMARY';
> ```

```sql T-SQL
-- Replace {database}, {path} placeholders
-- {database}: name of the database Streamkap should capture
-- {path}: path to data file directory for change data
USE {database};
GO
EXEC msdb.dbo.rds_cdc_enable_db '{database}'
GO

-- Microsoft recommends keeping CDC data files separate from your primary database files
ALTER DATABASE {database} ADD FILEGROUP Streamkap_ChangeTracking;
ALTER DATABASE {database} ADD FILE (
	NAME      = Streamkap_ChangeTracking_Data,
	FILENAME  = N'{path}\Streamkap_ChangeTracking_Data.ndf'
) TO FILEGROUP Streamkap_ChangeTracking;
GO
```



## Enable CDC on tables

For every table in the database you want Streamkap to capture, copy paste the script below into SQL Server Management Studio or Azure Data Studio, change placeholders as needed, and then run all queries.

```sql T-SQL
-- Replace {database}, {schema} and {table} placeholders
-- {database}: name of the CDC enabled database
-- {schema}: name of the schema with tables to CDC enable
-- {table}: name of the table to CDC enable
USE {database};
GO
EXEC sys.sp_cdc_enable_table
@source_schema        = N'{schema}',
@source_name          = N'{table}',
@role_name            = N'streamkap_connector',
@filegroup_name       = N'Streamkap_ChangeTracking',
@supports_net_changes = 0
GO
```



### Managing table change data access

The Table CDC enabling script above includes a named role option. This option can be used to limit which users' have access to the change data.

If you set the role option to a role other than `streamkap_connector`, you must add the Streamkap database user created earlier to that role. Use the script below to do that.

```sql T-SQL
-- Replace {database} and {role} placeholders
-- {database}: name of the CDC enabled database
-- {role}: name of the role
USE {database};
GO
ALTER ROLE {role} ADD MEMBER streamkap_user;
GO
```



If set to `NULL`, no role is used to limit access to the change data.

If the role does not exist, an attempt is made to create a database role with the specified name. If the database user running the script is not authorized to create a role within the database, the stored procedure fails.

# Streamkap Setup

1. Go to [Sources](https://app.streamkap.com/sources) and choose **SQL Server on Amazon RDS**
2. Input the following information:

   1. **Name **- A unique and memorable name for this Connector

   2. **Endpoint** - The [endpoint ](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_ConnectToMicrosoftSQLServerInstance.html#sqlserver-endpoint)of your RDS SQL Server database instance

   3. **Username **(Case sensitive) - `streamkap_user` OR the username you chose

   4. **Source Databases** (Case sensitive) - A comma separated list of CDC enabled database names. For example, if the databases are `sales` and `accounts`, you'd enter `sales,accounts`

   5. **Source Tables** (Case sensitive) - A comma separated list of CDC enabled table names, including schema name. For example, if the tables are `sales.orders` and`accounts.invoices`, you'd enter `sales.orders,accounts.invoices`
3. Click **Save**

# SQL Server Schema Evolution

When CDC is enabled for a table and changes occur to it, change events are persisted to a 'change table' on the SQL Server database server. 

If you introduce a change in the structure of the source table, for example, by adding a new column, that change is **not ** reflected in the change table. 

For as long as the change table continues to use the outdated table structure, the Streamkap SQL Server Source is unable to capture change events for the table correctly.

You must intervene to refresh the change table structure because of the way that CDC is implemented in SQL Server.

## Refresh change table structure (Online)

The procedure for completing an **Online** refresh is simpler than running it Offline, and you can complete it without any downtime to your systems and Streamkap pipelines.

> 🚧 Online refresh limitation
> 
> A potential gap can occur after the source table structure changes in the source database, but before you refresh. 
> 
> During that interval, change events continue to be captured by the existing SQL Server change table and your Streamkap pipelines, so the change events keep the outdated table structure. 
> 
> For example, if you added a new column to a source table, change events that are produced before the change table is refreshed do not contain the new column. 
> 
> If this gap cannot be tolerated, an **Offline** refresh has to be performed. However, that means downtime for whatever made structural changes to your tables **and** your Streamkap pipelines. Please contact us if this is required.

For every source table that has changed, copy paste the script below into SQL Server Management Studio or Azure Data Studio, change placeholders as required, and then run all queries.

> 👍 
> 
> If you're not sure what `{refresh_table}` name to use, use `{schema}_{table}_v{N}`. For example, if the source table is `sales.orders` then you'd use `sales_orders_v2`

```sql T-SQL
-- Replace {database}, {schema} and {table} placeholders
-- {database}: name of the CDC enabled database
-- {schema}: name of the schema with tables to refresh
-- {table}: name of the table to refresh
-- {refresh_table}: a unique name for the refreshed change table
USE {database};
GO
EXEC sys.sp_cdc_enable_table
@source_schema        = N'{schema}',
@source_name          = N'{table}',
@role_name            = N'streamkap_connector',
@filegroup_name       = N'Streamkap_ChangeTracking',
@supports_net_changes = 0,
@capture_instance     = N'{refresh_table}'
GO
```



> ❗️ Refresh table limitation
> 
> There cannot be more than 2 change tables for every source table.
> 
> After refreshing a change table using the above script, confirm with Streamkap Support that your SQL Server Source has started streaming from the refreshed change table. Once confirmed, disable CDC on the outdated change table. Use the script below to do that.
> 
> ```sql T-SQL
> -- Replace {database}, {schema}, {table} and {refresh_table} placeholders
> -- {database}: name of the CDC enabled database
> -- {schema}: name of the schema with the table refreshed earlier
> -- {table}: name of the table refreshed earlier
> -- {refresh_table}: name of the previous refresh table, usually {schema}_{table}
> USE {database};
> GO
> EXEC sys.sp_cdc_disable_table
> @source_schema        = N'{schema}',
> @source_name          = N'{table}',
> @capture_instance     = N'{refresh_table}'
> GO
> ```

# Troubleshooting

## SQL Server Setup scripts failing

There can be many reasons for the Setup scripts to fail, but the scripts below can help you diagnose the issues.

```sql T-SQL
-- Replace {database} placeholder
-- {database}: name of the CDC enabled database
USE {database};
GO

SELECT name, database_id, source_database_id, compatibility_level, is_read_only, state, state_desc, is_in_standby, is_cleanly_shutdown, is_cdc_enabled, is_encrypted, replica_id
FROM sys.databases
WHERE name = '{database}' AND is_cdc_enabled=1;

EXEC sys.sp_cdc_help_change_data_capture
GO
```



If any of the queries return an **error ** or **no results**:

- Check you connected to the SQL Server database with an RDS [master user account](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/UsingWithRDS.MasterAccounts.html) or, a database user that has `DB_OWNER` role privileges
- If the `SELECT ... FROM sys.databases ...` returns **no results**, the database you want Streamkap to capture may not be CDC enabled
- If the `EXEC sys.sp_cdc_help_change_data_capture` stored procedure returns **no results**, the source tables you want Streamkap to capture may not be CDC enabled

If you are still having issues after following the above steps, please don't hesitate to reach out to us.

## Two capture instances already exist for source table

If you're getting this error message when refreshing the change table structure, it's because there cannot be more than 2 change tables for every source table.

To fix the problem, 1 of the 2 change tables for the source table need to be disabled. The scripts below can help you do that.

```sql T-SQL
-- Replace {database}, {schema} and {table} placeholders
-- {database}: name of the CDC enabled database
-- {schema}: name of the schema with the table refreshed earlier
-- {table}: name of the table refreshed earlier
USE {database};
GO

EXEC sys.sp_cdc_help_change_data_capture
@source_schema = N'{schema}',
@source_name   = N'{table}'
GO
```



The above script should return 2 results, the 2 change tables for the `{table}` specified. Typically you would disable the oldest change table, so use the `create_date` column to identify the oldest one.

When you've identified the change table to disable, use its`source_schema`, `source_table` and `capture_instance` names in the query below and execute. Then, try your refresh table script again.

```sql T-SQL
-- Replace {database}, {schema}, {table} and {refresh_table} placeholders
-- {database}: name of the CDC enabled database
USE {database};
GO
EXEC sys.sp_cdc_disable_table
@source_schema        = N'{source_schema}',
@source_name          = N'{source_table}',
@capture_instance     = N'{capture_instance}'
GO
```