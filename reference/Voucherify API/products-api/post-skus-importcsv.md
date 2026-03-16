---
title: Import SKUs using CSV
excerpt: >-
  Import SKUs into the repository using a CSV file.


  The CSV file has to include headers in the first line. All properties which
  cannot be mapped to standard SKU fields will be added to the metadata object.
  You can find an example template
  [here](https://s3.amazonaws.com/helpscout.net/docs/assets/5902f1c12c7d3a057f88a36d/attachments/627b98d08c9b585083488a4c/Import_SKUS_template.csv). 


  Curl Example

  <!--

  title: "Example Request"

  lineNumbers: true

  -->

  ```cURL

  curl -X POST \
    https://api.voucherify.io/v1/skus/importCSV \
    -F file=@/path/to/skus.csv \
    -H "X-App-Id: c70a6f00-cf91-4756-9df5-47628850002b" \
    -H "X-App-Token: 3266b9f8-e246-4f79-bdf0-833929b1380c"
  ```

  > 🚧 Import sequence

  >

  > First import products using the [dedicated
  endpoint](ref:import-products-using-csv), then import SKUs using this endpoint
  to properly match SKUs to products.


  <!-- theme: info -->


  > 📘 Standard SKU fields mapping

  >

  > - **Required** fields are source_id and product_id.

  > - Supported CSV file headers:
  `product_id,sku,source_id,price,image_url,attributes`

  > - SKU **source_id**'s must be unique in the entire product catalog, no
  duplicates allowed.

  > - SKU attributes need to be in the form of a stringy-fied json,
  i.e.`"{'color':'blue'}"`. These attributes must be defined in the **product**
  beforehand in order for you to be able to import them to the SKU.

  > - You can use this method to update the following parameters in bulk:
  **sku** and the sku **price**.


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
  operationId: post-skus-importCSV
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---