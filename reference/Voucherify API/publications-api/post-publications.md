---
title: Create Publication
excerpt: >-
  This method selects vouchers that are suitable for publication, adds a publish
  entry and returns the publication.


  A voucher is suitable for publication when it's active and hasn't been
  published yet.  


  <!-- theme: warning -->

  > 🚧 Clearly define the source of the voucher

  >

  > You must clearly define which source you want to publish the voucher code
  from. It can either be a code from a campaign or a specific voucher identified
  by a code.  

  <!-- theme: warning -->

  > 🚧 Publish multiple vouchers

  > In case you want to publish multiple vouchers within a single publication,
  you need to specify the campaign name and number of vouchers you want to
  publish.  

  <!-- theme: info -->


  > 📘 Auto-update campaign

  >

  > In case you want to ensure the number of publishable codes increases
  automatically with the number of customers, you should use an **auto-update**
  campaign.
api:
  file: voucherify-api.json
  operationId: post-publications
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---