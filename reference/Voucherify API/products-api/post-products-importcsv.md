---
title: Import Products using CSV
excerpt: >-
  Import products into the repository using a CSV file.  


  Curl Example

  <!--

  title: "Example Request"

  lineNumbers: true

  -->

  ```cURL

  curl -X POST \
    https://api.voucherify.io/v1/products/importCSV \
    -F file=@/path/to/products.csv \
    -H "X-App-Id: c70a6f00-cf91-4756-9df5-47628850002b" \
    -H "X-App-Token: 3266b9f8-e246-4f79-bdf0-833929b1380c"
  ```


  The CSV file has to include headers in the first line.


  <!-- theme: info -->


  > 📘 Standard product fields mapping

  >

  > - Create a **comma separated value (CSV) file** or download our CSV import
  template. You can find an example template
  [here](https://s3.amazonaws.com/helpscout.net/docs/assets/5902f1c12c7d3a057f88a36d/attachments/627b82ed68d51e779443f550/Import_products_template.csv).

  > - Supported CSV file headers:
  `name,source_id,price,attributes,image_url,Metadata_property_name`

  > - **Name** is a **required** field. The remaining fields in the CSV template
  are optional.

  > - Override/Update products' **names** in Voucherify using this method. Data
  will be updated for each product included in the CSV file whose **source_id**
  matches a source ID in Voucherify. No other data can be updated other than the
  product name.

  > - Note that dates and date-time attributes need to be provided in compliance
  with the **ISO 8601 norms**. For example, 2022-03-11T09:00:00.000Z or
  2022-03-11

  >    - `YYYY-MM-DD`

  >    - `YYYY-MM-DDTHH`

  >    - `YYYY-MM-DDTHH:mm`

  >    - `YYYY-MM-DDTHH:mm:ss`

  >    - `YYYY-MM-DDTHH:mm:ssZ`

  >    - `YYYY-MM-DDTHH:mm:ssZ`

  >    - `YYYY-MM-DDTHH:mm:ss.SSSZ`

  > - Columns that can't be mapped to standard fields, will be mapped to
  **Custom attributes** and added as **products' metadata**. There is no limit
  on the number of custom attributes that you can import as metadata. 

  > - To provide the proper data type, you need to add all custom attributes to
  the metadata schema **before importing the file**. Read more
  [here](https://support.voucherify.io/article/99-schema-validation-metadata#add-metadata).

  > - **Product attributes** (not custom attributes) need to be separated by a
  comma and enclosed in double quotes, i.e "attribute1,attribute2".

  > - Headers with metadata names **can't contain white-space characters**.

  > - If you import metadata defined in the schema as **arrays (multiple)**, you
  need to separate each value using a comma, for example:  

  >    - array of strings: "subscribed,premium"  

  >    - array of numbers: "123,234". 

  >    - array of dates: "2000-01-01,2000-01-02"


  This API request starts a process that affects Voucherify data in bulk. 


  In case of small jobs (like bulk update) the request is put into a queue and
  processed once every other bulk request placed in the queue prior to this
  request is finished. However, when the job takes a longer time (like vouchers
  generation) then it is processed in small portions in a round-robin fasion.
  When there is a list of vouchers generation scheduled, then they will all have
  the `IN_PROGRESS` status shortly. This way, small jobs added just after
  scheduling big jobs of the same type will be processed in a short time
  window. 


  The result will return the async ID. You can verify the status of your request
  via this [API request](ref:get-async-action).
api:
  file: voucherify-api.json
  operationId: post-products-importCSV
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---