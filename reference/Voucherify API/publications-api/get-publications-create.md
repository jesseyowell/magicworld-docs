---
title: Create Publication
excerpt: >-
  This method selects vouchers that are suitable for publication, adds a publish
  entry and returns the publication.


  A voucher is suitable for publication when it's active and hasn't been
  published yet.

  > ❗️ Limited access

  >

  > Access to this endpoint is limited. This endpoint is designed for specific
  integrations and the API keys need to be configured to access this endpoint.  


  <!-- theme: warning -->

  > 🚧 Clearly define the source of the voucher

  >

  > You must clearly define which source you want to publish the voucher code
  from. It can either be a code from a campaign or a specific voucher identified
  by a code.  

  <!-- theme: warning -->

  > 🚧 Publish multiple vouchers

  > This endpoint does not support the publishing of multiple vouchers from a
  single campaign. In case you want to publish multiple vouchers within a single
  publication, you need to use a [dedicated endpoint](ref:create-publication).  

  <!-- theme: info -->


  > 📘 Specifying the voucher to be published

  >

  > - In case you want to ensure the number of publishable codes increases
  automatically with the number of customers, you should use an **auto-update**
  campaign and in the query parameters specify the `campaign` without specifying
  the voucher.

  > - If you would like to publish a specific code from a specific campaign,
  then you need to provide the `campaign` and the `voucher` parameters.

  > - If you would like to publish a standalone voucher, then omit the campaign
  parameter and simply provide the `voucher` parameter.
api:
  file: voucherify-api.json
  operationId: get-publications-create
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---