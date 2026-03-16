---
title: Update Campaign
excerpt: >-
  Updates the specified campaign by setting the values of the parameters passed
  in the request body. Any parameters not provided in the payload will be left
  unchanged. 


  Fields other than the ones listed in the request body won't be modified. Even
  if provided, they will be silently skipped.   

  <!-- theme: warning -->

  > #### Vouchers will be affected

  >

  > This method will update vouchers aggregated in the campaign. It will affect
  all vouchers that are not published or redeemed yet.
api:
  file: voucherify-api.json
  operationId: put-campaigns-campaignId
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---