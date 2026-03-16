---
title: Redeem Voucher (client-side)
excerpt: >-
  To redeem a voucher, you need to create a redemption object. It increments the
  redemption counter and updates the history of the voucher. This method is
  accessible through public keys, which you can use in client-side apps (mobile
  and web browser apps). 


  <!-- theme: danger -->

  > ❗️ Important  

  >

  > This endpoint supports the redemption of a single promo code. If you need to
  redeem more than one incentive, you can use the Stackable discounts API. The
  <!-- [stacking discounts API](OpenAPI.json/paths/~1redemptions/post)
  -->[stacking discounts API](ref:redeem-stacked-discounts) lets you redeem up
  to 5 incentives per call. Before integrating with Voucherify, choose which
  redemption endpoint you prefer to use.


  The client-side redemption works similar to the server-side <!-- [voucher
  redemption](OpenAPI.json/paths/~1vouchers~1{code}~1redemption/post)
  -->[voucher redemption](ref:redeem-voucher) endpoint. The difference lies in
  the authorization. For the client-side, you can use client-side keys.


  <!-- theme: important -->

  > 📘 Opt-in  

  >

  > By default this feature is disabled. If you want to use it, you will need to
  enable the function explicitly in **Project Settings**.


  <!-- theme: danger -->

  > ❗️ Security Threat  

  >

  > Be careful if you want to include the voucher redemption functionality
  directly on your client side (website or mobile app). In this configuration,
  there is a chance that discounts can be modified before being sent to the
  server.


  ### Expand Response

  You may expand the response by adding the following object to your request
  body. The expanded response will include the category details of the voucher.


  ```json

  {
      "options": {
          "expand": [
              "category"
          ]
      }
  }

  ```
api:
  file: voucherify-api.json
  operationId: post-redeem
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---