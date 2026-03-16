---
title: List Redemptions
excerpt: >-
  Returns a list of redemptions previously created. The redemptions are returned
  in a sorted order, with the most recent redemptions appearing first. The
  response returns a list of redemptions of all vouchers. 


  ## Filtering results

  The result can be narrowed according to specified (or default) filters, for
  example, you can sort redemptions by date:

  `https://api.voucherify.io/v1/redemptions?limit=3&[created_at][before]=2017-09-08T13:52:18.227Z`.
  A filter based on the object `created_at` field narrows down the results and
  lists redemptions done before or after a particular date time. You can use the
  following options: `[created_at][after]`, `[created_at][before]`. A date value
  must be presented in ISO 8601 format (`2016-11-16T14:14:31Z` or `2016-11-16`).
  An example: `[created_at][before]=2017-09-08T13:52:18.227Z`.


  ## Failed Redemptions


  A redemption may fail for various reasons. You can figure out an exact reason
  from the `failure_code`:

  - `resource_not_found` - voucher with given code does not exist

  - `voucher_not_active` - voucher is not active yet (before start date)

  - `voucher_expired` - voucher has already expired (after expiration date)

  - `voucher_disabled` -  voucher has been disabled (`active: false`)

  - `quantity_exceeded` - voucher's redemptions limit has been exceeded

  - `gift_amount_exceeded` - gift amount has been exceeded

  - `customer_rules_violated` - customer did not match the segment

  - `order_rules_violated` - order did not match validation rules

  - `invalid_order` - order was specified incorrectly

  - `invalid_amount` - order amount was specified incorrectly

  - `missing_amount` - order amount was not specified

  - `missing_order_items` - order items were not specified

  - `missing_customer` - customer was not specified
api:
  file: voucherify-api.json
  operationId: get-redemptions
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---