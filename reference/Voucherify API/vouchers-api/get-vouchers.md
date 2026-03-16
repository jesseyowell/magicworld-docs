---
title: List Vouchers
excerpt: >-
  Returns a list of your vouchers. By default, the vouchers are returned sorted
  by creation date, with the most recent vouchers appearing first. A maximum of
  10 vouchers are returned in the response.


  When you get a list of vouchers, you can optionally specify query parameters
  to customize the amount of vouchers returned per call using `limit`, which
  page of vouchers to return using `page`, sort the vouchers using the `order`
  query parameter and more.


  This method will return an error when trying to return a limit of more than
  100 vouchers.
api:
  file: voucherify-api.json
  operationId: get-vouchers
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---