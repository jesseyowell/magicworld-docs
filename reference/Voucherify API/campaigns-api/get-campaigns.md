---
title: List Campaigns
excerpt: >-
  Retrieve a list of campaigns in a project. 


  The campaigns are returned sorted by creation date, with the most recent
  campaigns appearing first.  


  When you get a list of campaigns, you can optionally specify query parameters
  to customize the amount of campaigns returned per call using `limit`, which
  page of campaigns to return using `page`, sort the campaigns using the `order`
  query parameter and filter the results by the `campaign_type`.


  This method will return an error when trying to return a limit of more than
  100 campaigns.
api:
  file: voucherify-api.json
  operationId: get-campaigns
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---