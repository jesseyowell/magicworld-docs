---
title: Import Vouchers using CSV
excerpt: >-
  Import standalone vouchers into the repository using a CSV file.


  The CSV file has to include headers in the first line. All properties listed
  in the file headers that cannot be mapped to standard voucher fields will be
  added to the metadata object.  


  You can find an example CSV file
  [here](https://support.voucherify.io/article/45-import-codes-and-share-them-digitally#coupons).

  ___

  <!--

  title: "cURL Example Request"

  lineNumbers: true

  -->

  ```cURL cURL example

  curl -X POST \
    https://api.voucherify.io/v1/vouchers/importCSV \
    -F file=@/path/to/vouchers.csv \
    -H "X-App-Id: c70a6f00-cf91-4756-9df5-47628850002b" \
    -H "X-App-Token: 3266b9f8-e246-4f79-bdf0-833929b1380c"
  ```


  <!-- theme: info -->


  > 📘 Standard voucher fields mapping

  >

  > - Go to the <!-- [import vouchers](OpenAPI.json/paths/~1vouchers~1import)
  -->[import vouchers](ref:import-vouchers) endpoint to see all standard CSV
  fields description (body params section).

  > - Supported CSV file headers: Code,Voucher Type,Value,Discount
  Type,Category,Start Date,Expiration Date,Redemption Limit,Active,Additional
  Info,Custom Metadata Property Name

  >- **Start and expiration dates** need to be provided in compliance with the
  ISO 8601 norms. For example, 2020-03-11T09:00:00.000Z.  

  >    - `YYYY-MM-DD`

  >    - `YYYY-MM-DDTHH`

  >    - `YYYY-MM-DDTHH:mm`

  >    - `YYYY-MM-DDTHH:mm:ss`

  >    - `YYYY-MM-DDTHH:mm:ssZ`

  >    - `YYYY-MM-DDTHH:mm:ssZ`

  >    - `YYYY-MM-DDTHH:mm:ss.SSSZ`

  > - Custom code attributes (not supported by-default) need to be added as code
  **metadata**.

  > - You **cannot import the same codes** to a single Voucherify Project.


  <!-- theme: info -->


  > 📘 Categories

  >

  > In the structure representing your data, you can define a category that the
  voucher belongs to. You can later use the category of a voucher to group and
  search by specific criteria in the Dashboard and using the [List
  Vouchers](ref:list-vouchers) endpoint.


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
  operationId: post-vouchers-importCSV
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---