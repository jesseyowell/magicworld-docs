---
title: Validate Promotion Tier
excerpt: >-
  To verify whether the promotion tier discount can be applied to an order. This
  method is designed for server side integration which means that it is
  accessible only through private keys.


  <!-- theme: danger -->

  > ❗️ Important  

  >

  > This endpoint supports the validation of a single promotion tier. If you
  need to validate more than one incentive, you can use the <!-- [Stackable
  discounts API](OpenAPI.json/paths/~1validations/post) -->[Stackable discounts
  API](ref:validate-stacked-discounts). The stacking discounts API lets you
  validate up to 5 incentives per call. Before integrating Voucherify, choose
  which validation endpoint you prefer to use.
api:
  file: voucherify-api.json
  operationId: post-promotions-tiers-tierId-validation
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---