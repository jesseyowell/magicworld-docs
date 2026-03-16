---
title: Redeem Promotion
excerpt: >-
  To redeem a promotion, you create a redemption object passing a context.


  You can retrieve a list of active promotions through the <!-- [Validate
  Promotions](OpenAPI.json/paths/~1promotions~1validation/post) -->[Validate
  Promotions](ref:validate-promotions) endpoint. That validation method will
  return a list of active​ promotion tiers identified by thier IDs.  


  <!-- theme: danger -->

  > ❗️ Important  

  >

  > This endpoint supports the redemption of a single promo code. If you need to
  redeem more than one incentive, you can use the Stackable discounts API. The
  <!-- [stacking discounts API](OpenAPI.json/paths/~1redemptions/post)
  -->[stacking discounts API](ref:redeem-stacked-discounts) lets you redeem up
  to 5 incentives per call. Before integrating with Voucherify, choose which
  redemption endpoint you prefer to use.


  > 📘 Redemption rollback

  >

  > Do you need to undo a redemption? You can do it with <!-- [redemption
  rollback](OpenAPI.json/paths/~1redemptions~1{redemptionId}~1rollback/post)
  -->[redemption rollback](ref:rollback-redemption).
api:
  file: voucherify-api.json
  operationId: post-promotions-tiers-promotionTierId-redemption
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---