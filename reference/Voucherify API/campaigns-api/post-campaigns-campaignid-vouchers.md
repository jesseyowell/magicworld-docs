---
title: Add Vouchers to Campaign
excerpt: >-
  This method gives the possibility to push new vouchers to an existing
  campaign. New vouchers will inherit properties from the campaign profile.
  However, it is possible to overwrite some of them in the request body. If you
  provide an optional `code_config` parameter with a voucher code configuration,
  then it will be used to generate new voucher codes. Otherwise, the voucher
  code configuration from the campaign will be used.


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
  operationId: post-campaigns-campaignId-vouchers
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---