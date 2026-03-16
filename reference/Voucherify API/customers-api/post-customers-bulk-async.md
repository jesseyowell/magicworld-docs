---
title: Update Customers in bulk
excerpt: >-
  Update several customers in one asynchronous operation. 


  In one request, it is possible to update a maximum of **100** records. In the
  response body, you get a unique async action identifier.  


  If a requested customer object is not found, then an **upsert** occurs. This
  is reflected in the <!-- [Get Async
  Action](OpenAPI.json/paths/~1async-actions~1{asyncActionId}/get) -->[Get Async
  Action](ref:get-async-action) endpoint as follows:  


  <!--

  title: "Response"

  lineNumbers: true

  -->

  ```json

  {
      "found": false,
      "updated": true
  }

  ```


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
  operationId: post-customers-bulk-async
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---