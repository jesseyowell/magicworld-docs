---
title: Examine Qualification
excerpt: >-
  The method can be used for sending a request to display all campaigns
  qualified to the given customer and context (e.g., order). 


  The maximum number of **returned campaigns is 50**.


  ## What campaign types are included in the response?


  - `DISCOUNT_COUPONS`

  - `GIFT_VOUCHERS`

  - `REFERRAL_PROGRAM`


  ## What's excluded?


  A checking logic will be run only among campaigns and will ignore _standalone
  vouchers_. For standalone vouchers, you should run a [dedicated
  endpoint](ref:examine-vouchers-qualification) for searching and identifing
  vouchers. 


  ## Subsequent Steps


  As a recommended subsequent step after selecting a qualified campaign is to
  publish a voucher code from that campaign. The [API method for
  publishing](ref:create-publication) will return a unique code which will
  belong to a given customer.


  ## Sample use case


  As a sample use case, you can imagine a requirement of displaying coupons
  (grouped in campaigns) that a customer is eligible to use. The customer should
  get assigned to the particular voucher from the campaign and then may redeem
  that particular code when he/she places an order.<!--
  [Read](https://docs.voucherify.io/docs/checking-eligibility-for-coupons)-->


  [Read](doc:checking-eligibility-for-coupons) about Qualification API limits
  before you start.
api:
  file: voucherify-api.json
  operationId: post-campaigns-qualification
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---