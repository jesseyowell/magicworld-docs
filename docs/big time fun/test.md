---
title: Test
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Primis Platform API is a tool for third-party developers, which allows integration with Primis’ backend data to their systems. Currently, this API provides the following capabilities:

* Reporting (e.g., impressions, revenue, RPM / eCPM etc.)

> 📘 How to work with Primis Platform API
>
> Check this walkthrough [**here**](https://docs.primis.tech/recipes/platform-api) for a quick explanation.

**API Architecture**\
The Primis Platform API is implemented as an API over the HTTPS protocol and returns (by default) JSON data format.

**API Versioning**\
Primis releases versions of this API in accordance with the following rule to protect the users from integration problems that may occur in the future.

* It is guaranteed that changes within the same major version of the API (e.g., 1.00, 1.10, etc.) will not break your integration and will only fix defects or add minor feature enhancements or changes.
* Major version changes (e.g., 2.00, 3.00, etc.) may introduce some significant changes that may require some coding changes to your integration. In other words, integrations written to be used with version 1.0 may not work with version 2.0 or 3.0, without possible significant changes.

**Connections**\
Connections to Primis API are only accessible via the HTTPS protocol.

**Errors**\
Primis Platform API returns errors in standard HTTP status codes (usually client error codes, e.g. 4XX status codes). See the Errors Description section of this document for details for each error returned by the service.

## Authentication

All interactions with Primis Platform API **must be authenticated**. An API client can be authenticated by the platform by performing an initial login request using an API User Name and Code. This login request will return a token code and the calling client must send this token code in all other service requests.

* To access the Primis Platform API, the calling system must authenticate and use the authentication token in subsequent API requests. 

* To receive credentials for Primis Platform API, contact your assigned account manager.

* The token code will expire after one hour. After this time the user must re-authenticate using Step 1 as described below.

The Authentication service uses HTTPS GET method. 

**Step 1**: To perform the authentication you need to send a GET request:

```curl
curl "https://console.primis.tech/UI/php/responders/apiResponder.php?method=authentication&apiUserName=[API_USER_NAME]&apiUserCode=[API_USER_CODE]&version=2.19"
```

Primis Platform API responds with a JSON containing your API access token: 

```json
{"token":" XXXXXXXXXXXXX "}
```

## Reporting Service

The reporting service is a non-blocking service. The service is providing statistical data by chosen granularity (e.g. browser, OS, specific placement, etc.) In the current version, the service provides Primis Publisher Reports by the appropriate method, as is shown below.

**Request**\
To receive the report data, you need to send 2 commands consequentially:

Step 1: Posting a report request which includes a token, version, method and JSON formatted filters. Hereupon, the API will return a unique ‘Report ID’. 

For more information regarding the possible filters, their description and syntax, see the Report Request Filters section. For the full filter list, see the Reference: Filters Description section of the current document.

An example:

```curl
curl -X POST -d 'token=XXXXXXXXXXXXX&version=2.19&method=publisherReport&data=[{"name":"filter1","data":["nnn"]},{"name":"filter2","data":"123"}]' -f https://console.primis.tech/UI/php/responders/apiResponder.php
```

Token = XXXXXXXXXXXXX\
Version = 2.19\
Method = publisherReport\
Data =\
\[\
\{"name":"filter1","data":\["nnn"]},\
\{"name":"filter2","data":"123"}\
]

A report ID is returned as an answer:

```curl
{"reportId":"0123456789"}
```

**Step 2**: Requesting a report data by Report ID, which consists of token, version, method and report ID.\
A command example:

```curl
curl --data "token=XXXXXXXXXXXXX&version=2.19&method=publisherReport&reportId=0123456789" -f https://console.primis.tech/UI/php/responders/apiResponder.php
```

Token = XXXXXXXXXXXXX\
Version = 2.19\
Method = publisherReport\
Report ID = 0123456789

**Response**\
After the Step 2 request, the API will return a response. 

The response is represented as an array of element objects in JSON format, where objects are defined by your requested dimensions and set of fields inside an element are set by the metrics in your request. The returned report data depends on your selected filters that were set in Step 1.

* When the data is ready, the Primis Platform API will return the requested data.
* If the report data is not yet ready, the API will return ‘Data is not ready’ (#454) error. In such a case please repeat Step 2 several minutes later.

Data example:

```json
[
{
"placement":1111,
"placementName":"Placement Name1",
"placement_imps":1111,
"rpm":0.1,
"revenue":11.11
},
{
"placement":2222,
"placementName":"Placement Name2",
"placement_imps":2222,
"rpm":0.2,
"revenue":22
}
]
```

Note: The time zone and currency of the report data are the account’s default time zone and currency.

**Report Request Filters**\
The report request filters are designed to determine the resulting data. Each filter must consist of a name, data and optional include/exclude parameter.

The data field of a filter might be either a single value or an array of values depending on the filter. The exclude field should be set to ‘1’ (exclude) or ‘0’ (include).

All the API filters can be divided into several groups by their meaning:

**1. Report Type**\
(API name: ”reportType”)\
This filter determines which report you can get. Report type might be: Media, Ad Server, Content, *Syndication* or *Billing*.\
Each report type has its own set of metrics and dimensions.

**2. Dimensions**\
(API name: ”dimensions”)\
The dimensions filter determines the desirable objects in your report response, i.e. what objects are needed to be “grouped by”. Placement, Campaign, Browser and Country are dimension examples. Each report type has its own dimensions set.

**3. Metrics**\
(API name: ”metrics”)\
Metrics are different types of quantitative measurement parameters, by which Primis collects statistics, e.g. Attempts, Impressions or Revenue\
**4.Object Filters**\
(all other filters)\
All other available filters are optional and are used to filter the report data, i.e. to see only such data you want to be displayed, whether it is a specific set of your placements or statistical data for a specific country.

For the full filter list and its parameters, see the **Filters Description** section in Reference.

## Report Types

**Media Report**\
A Media Report is a generic report type that provides statistics in different levels of granularity from the media side. To have access to the Media Report type, your Primis account must be setup as Publisher\`s account.

Media Reports support the following dimensions: placement; player type; media type; placement size; browser; operating system; operating system version; country; device type; domain; total; time interval and sub ID. Please note that the 'total' dimension can't be used in combination with any other, but only as a single dimension.

Its metrics are (API names are given in parentheses): ID and name (`id` and `name` metrics will return the corresponded dimension data); placement impressions (placement\_imps); revenue (revenue); revenue RPM (rpm); Ad Server video impressions from publisher\`s Ad Server campaigns (video\_adserver\_imps); Ad Server video revenue (video\_adserver\_revenue); revenue from the Primis Marketplace side (video\_primis\_revenue); Ad Server video eCPM (video\_adserver\_cpm) and others.

For the full list of filters and their syntax and parameters see the Filter Descriptions section in Reference.

A request example:

```curl
curl -X POST -d 'token=XXXXXXXXXXXXX&version=2.19&method=publisherReport&data=[{"name":"reportType","data":"media"},{"name":"timeZone","data":"us_eastern"},{"name":"dimensions","data":["browser"]},{"name":"period","data":"lastMonth"},{"name":"metrics","data":["id","name","placement_imps","rpm","revenue"]}]' -f https://console.primis.tech/UI/php/responders/apiResponder.php
```

A response example:

```json
[
{
"deviceTypeId":"smartphone_web",
"placement_imps":1111,
"rpm":0.1,
"revenue":11.11
},
{
"deviceTypeId":"Desktop",
"placement_imps":22222,
"rpm":2.2,
"revenue":222
},
{
"deviceTypeId":"tablet_app",
"placement_imps":33333,
"rpm":3.3,
"revenue":333.33
},
]
```

**Ad Server Report**\
An Ad Server report is a video statistic report adjusted to provide granularity for Ad Server campaigns. The Ad Server report requires an Ad Server access for your Primis account.

The Ad Server report\`s dimensions are: media placement; media type; campaign; browser; placement size; player type; operating system; operating system version; hb partner; country; device type; domain; total and time interval. Please note that the 'total' dimension can't be used in combination with any other, but only as a single dimension.

Its metrics are (API names are given in parentheses): ID and name (`id` and `name` metrics will return the corresponded dimension data); video ad impressions (ad\_imps); eCPM (ad\_cpm); revenue (ad\_revenue); percent of viewable impressions (ad\_viewability\_rate); ad attempts (ad\_attempts); completion rate (ad\_vtr) and fillrate (ad\_fillrate); Ad Server Commission Fee (serving\_fee) and others.

For the full list of filters and their syntax and parameters see the Filter Descriptions section in Reference.

A request example:

```curl
curl -X POST -d 'token=XXXXXXXXXXXXX&version=2.19&method=publisherReport&data=[{"name":"reportType","data":"adServer"},{"name":"timeZone","data":"us_eastern"},{"name":"dimensions","data":["browser"]},{"name":"period","data":"custom"},{"name":"fromDay","data":"2018-10-20"},{"name":"toDay","data":"2018-10-21"},{"name":"timeInterval","data":"cumulative"},{"name":"metrics","data":["id","name","ad_imps","ad_cpm","ad_revenue"]}]' -f https://console.primis.tech/UI/php/responders/apiResponder.php
```

A response example:

```json
[
{
"browserId":"Mobile Application",
"ad_imps":1111,
"ad_cpm":1.1,
"ad_revenue":11.11
},
{
"browserId":"Chrome",
"ad_imps":2222,
"ad_cpm":2.2,
"ad_revenue":222.22
},
]
```

**Content Report**\
A Content report is a content statistic report. To have access to the Content Report type, your Primis account must be setup as Publisher\`s account.

The Content report\`s dimensions are: placement; placement size; media type; content channel; channel category; content creator; content file; browser; operating system; operating system version; country; device type; domain; total and time interval. Please note that the 'total' dimension can't be used in combination with any other, but only as a single dimension.

Its metrics are (API names are given in parentheses): ID and name (`id` and `name` metrics will return the corresponded dimension data); content impressions (content\_imps); content eCPM (content\_ecpm); playlist click rate (content\_playlist\_click\_rate); complete rate (content\_complete\_rate); likes (content\_likes); pause click rate (content\_pause\_click\_rate) and others.

For the full list of filters and their syntax and parameters see the Filter Descriptions section in Reference.

A request example:

```curl
curl -X POST -d 'token=XXXXXXXXXXXXX&version=2.18&method=publisherReport&data=[{"name":"reportType","data":"content"},{"name":"timeZone","data":"us_eastern"},{"name":"dimensions","data":["browser"]},{"name":"period","data":"yesterday"},{"name":"timeInterval","data":"cumulative"},{"name":"metrics","data":["id","name","content_imps"]}]' -f https://console.primis.tech/UI/php/responders/apiResponder.php
```

A response example:

```json
[
{
"browserId":"Mobile Application",
"content_imps":1111,
},
{
"browserId":"Chrome",
"content_imps":2222,
},
{
"browserId":"Opera",
"content_imps":3333,
},
]
```

**Syndication Report**\
A Syndication report is a syndication content statistic report. To have access to the Syndication Report type, your Primis account must be setup as Publisher\`s account.

The Syndication report\`s dimensions are: country; media type; content channel; channel category; content file; browser; operating system; domain; total and time interval. Please note that the 'total' dimension can't be used in combination with any other, but only as a single dimension.

Its metrics are (API names are given in parentheses): ID and name (`id` and `name` metrics will return the corresponded dimension data); content impressions (content\_imps); content eCPM (content\_ecpm); playlist click rate (content\_playlist\_click\_rate); complete rate (content\_complete\_rate); likes (content\_likes); pause click rate (content\_pause\_click\_rate) and others.

For the full list of filters and their syntax and parameters see the Filter Descriptions section in Reference.

A request example:

```curl
curl -X POST -d 'token=XXXXXXXXXXXXX&version=2.19&method=publisherReport&data=[{"name":"reportType","data":"syndication"},{"name":"timeZone","data":"us_eastern"},{"name":"dimensions","data":["browser"]},{"name":"period","data":"yesterday"},{"name":"timeInterval","data":"cumulative"},{"name":"metrics","data":["id","name","content_imps"]}]' -f https://console.primis.tech/UI/php/responders/apiResponder.php
```

A response example:

```json
[
{
"browserId":"Mobile Application",
"content_imps":1111,
},
{
"browserId":"Chrome",
"content_imps":2222,
},
{
"browserId":"Opera",
"content_imps":3333,
},
]
```

**Billing Report**\
A Billing Report is a report type that provides billing data, similar to the Billing newTerm of the Primis system. The Billing Report requires Ad Server access for your Primis account.\
Except for the Report Type, no other filters are necessary for the Billing Report. All other filters in the request will be ignored.

A request example:

```curl
curl --data 'token=XXXXXXXXXXXXX&version=2.19&method=publisherReport&data=[{"name":"reportType","data":"billing"}]' -f https://console.primis.tech/UI/php/responders/apiResponder.php
```

As a response, the API will return the user\`s billing data under the fixed metrics.

Below you can find the set of metrics.

| Name              | API Name        | Format             |
| :---------------- | :-------------- | :----------------- |
| Period start date | startDate       | Date: `yyyy-mm-dd` |
| Period end date   | endDate         | Date: `yyyy-mm-dd` |
| Payment status    | status          | String             |
| Ad Server Revenue | adServerRevenue | Decimal            |
| Primis Revenue    | primisRevenue   | Decimal            |
| Total Revenue     | totalRevenue    | Decimal            |
| Ad Serving Fee    | adServingFee    | Decimal            |
| Payment Date      | paymentDate     | Date: `yyyy-mm-dd` |
| Net Billing       | netBilling      | Decimal            |

A response example:

```json
[
{
"startDate":"2018-11-01",
"endDate":"2018-11-24",
"status":"openPeriod",
"adServerRevenue":0,
"primisRevenue":0,
"totalRevenue":0,
"adServingFee":0,
"paymentDate":"-",
"netBilling:0"
},
{
"startDate":"2018-10-01",
"endDate":"2018-10-31",
"status":"invoiceReceived",
"adServerRevenue":1967.63,
"primisRevenue":4990.93,
"totalRevenue":6958.55,
"adServingFee":977.07,
"paymentDate":"2018-11-26",
"netBilling:2013.86"
},
{
"startDate":"2018-09-01",
"endDate":"2018-09-31",
"status":"paid",
"adServerRevenue":365.12,
"primisRevenue":3251.19,
"totalRevenue":6616.31,
"adServingFee":80.21,
"paymentDate":"2018-11-01",
"netBilling:2570.98"
},
]
```

<br />
