---
title: Create Campaign
excerpt: >-
  Method to create a batch of vouchers aggregated in one campaign. You can
  choose a variety of voucher types and define a unique pattern for generating
  codes.  

  <!-- theme: info -->


  > 📘 Global uniqueness

  >

  > All campaign codes are unique across the whole project. Voucherify will not
  allow you to generate 2 campaigns with the same coupon code.  

  <!-- theme: warning -->

  > 🚧 Code generation status

  >

  > This is an asynchronous action; you can't read or modify a newly created
  campaign until the code generation is completed. See the `creation_status`
  field in the <!-- [campaign
  object](OpenAPI.json/components/schemas/2_obj_campaign_object) -->[campaign
  object](ref:get-campaign) description.
api:
  file: voucherify-api.json
  operationId: post-campaigns
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---