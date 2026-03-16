---
title: Add Member
excerpt: >-
  This method assigns a loyalty card to a customer. It selects a <!-- [loyalty
  card](OpenAPI.json/components/schemas/1_obj_voucher_object) -->[loyalty
  card](ref:get-voucher) suitable for publication, adds a publish entry, and
  returns the published voucher.  


  A voucher is suitable for publication when it's active and hasn't been
  published yet.  


  <!-- theme: info -->

  > 📘 Auto-update campaign

  >

  > In case you want to ensure the number of publishable codes increases
  automatically with the number of customers, you should use **auto-update**
  campaign.
api:
  file: voucherify-api.json
  operationId: post-loyalties-campaignId-members
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---