---
title: Validate Voucher
excerpt: >-
  To verify a voucher code given by a customer, you can use this method. It is
  designed for a server side integration, which means that is accessible only
  through private keys.  


  <!-- theme: danger -->

  > ❗️ Important  

  >

  > This endpoint supports the validation of a single promo code. If you need to
  validate more than one incentive, you can use the <!-- [Stackable discounts
  API](OpenAPI.json/paths/~1validations/post) -->[Stackable discounts
  API](ref:stackable-discounts-api). The stacking discounts API lets you
  validate up to 5 incentives per call. Before integrating Voucherify, choose
  which validation endpoint you prefer to use.


  #### Gift Vouchers - validate Gift Card and control amount to redeem

  Voucherify also gives the possibility to create a gift card, which allows
  using credits to fulfill the order. A user can specify how many credits he
  wants to use from the gift card. The available balance of credits is counted
  based on policy rules attached to the Gift Voucher definition.  


  This operation returns information about the validity of the code. Moreover,
  it returns a hashed source identifier which can be used as a tracking ID in
  future calls.


  If a validation session is established, then the session details will be
  returned as well. Read more about sessions <!--
  [here](..docs/guides/campaign_recipes/Locking-Validation-Session.md)
  -->[here](doc:locking-validation-session).


  Voucher validation might fail because of one of these reasons:

  * `voucher not found` - voucher doesn't exist or was <!--
  [deleted](OpenAPI.json/paths/~1vouchers~1{code}/delete)
  -->[deleted](ref:delete-voucher)

  * `voucher expired` - voucher is out of start date - expiration date time
  frame

  * `voucher is disabled` - learn more about a <!-- [disabled
  voucher](OpenAPI.json/paths/~1vouchers~1{code}~1disable/post) -->[disabled
  voucher](ref:disable-voucher)

  * `customer does not match segment rules` - learn more [customer
  tracking](doc:customers#customer-tracking) 

  * `order does not match validation rules` - learn more about [validation
  rules](doc:validation-rules)
api:
  file: voucherify-api.json
  operationId: post-vouchers-code-validate
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---