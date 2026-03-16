---
title: Create Loyalty Campaign
excerpt: >-
  Creates a batch of <!-- [loyalty
  cards](OpenAPI.json/components/schemas/8_obj_loyalty_card_object) -->[loyalty
  cards](ref:get-member) aggregated in a single loyalty campaign. It also allows
  you to define a custom codes pattern.  


  <!-- theme: info -->

  > 📘 Global uniqueness

  > All codes are unique across the whole project. Voucherify won't allow to
  generate the same codes in any of your campaigns.


  <!-- theme: warning -->

  > 🚧 Asyncronous action!

  >

  > This is an asynchronous action, you can't read or modify a newly created
  campaign until the code generation is completed. See `creation_status` field
  in the <!-- [loyalty campaign
  object](OpenAPI.json/components/schemas/8_obj_loyalty_campaign_object)
  -->[loyalty campaign object](ref:get-loyalty-program) description.
api:
  file: voucherify-api.json
  operationId: post-loyalties
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---