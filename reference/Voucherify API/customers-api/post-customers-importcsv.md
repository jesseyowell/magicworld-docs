---
title: Import and Update Customers using CSV
excerpt: >-
  This API method lets you import or update customer data. To get a proper and
  valid response, please send a CSV file with data separated by commas.  


  ## Request Example

  <!--

  title: "Example Request"

  lineNumbers: true

  -->

  ```cURL

  curl -X POST \
    https://api.voucherify.io/v1/customers/importCSV \
    -F file=@/path/to/customers.csv \
    -H "X-App-Id: c70a6f00-cf91-4756-9df5-47628850002b" \
    -H "X-App-Token: 3266b9f8-e246-4f79-bdf0-833929b1380c"
  ```

  ## CSV File Format


  The CSV file has to include headers in the first line. All properties which
  cannot be mapped to standard customer fields will be added to the metadata
  object.


  <!-- theme: info -->

  > 📘 Standard customer fields mapping

  >

  > **No spaces allowed in field names**  

  > Name, Email, Phone, Birthdate, Source_id, Address_line_1, Address_line_2,
  Address_Postal_Code, Address_City, Address_State, Address_Country,
  Description, Metadata_name_1, Metadata_name_2


  ## Update Customers using CSV


  If you would like to update customer's data, you can do it using the CSV file
  with new data. However, remember to include a `source_id` in your CSV file to
  manage the update successfully.


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
  operationId: post-customers-importCSV
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---