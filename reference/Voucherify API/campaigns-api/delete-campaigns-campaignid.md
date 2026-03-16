---
title: Delete Campaign
excerpt: >-
  Permanently deletes a campaign and all related vouchers. This action cannot be
  undone. Also, this method immediately removes any redemptions on the voucher.


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
  operationId: delete-campaigns-campaignId
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---