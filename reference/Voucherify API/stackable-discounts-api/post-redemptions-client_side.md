---
title: Redeem Stackable Discounts (client-side)
excerpt: >-
  Use this method to redeem up to 5 redeemables in a single API request. This
  method is accessible through public keys which you can use in client side
  requests coming from mobile and web browser applications.


  ## How API returns calculated discounts and order amounts in the response


  In the table below, you can see the logic the API follows to calculate
  discounts and amounts:


  | **Field** | **Calculation** | **Description** |

  |:---|:---|:---|

  | amount | N/A | This field shows the order amount before applying any
  discount |

  | total_amount | `total_amount` = `amount` - `total_discount_amount` | This
  field shows the order amount after applying all the discounts |

  | discount_amount | `discount_amount` = `previous_discount_amount` +
  `applied_discount_amount` | This field sums up all order-level discounts up to
  and including the specific discount being calculated for the stacked
  redemption. |

  | items_discount_amount | sum(items, i => i.discount_amount) | This field sums
  up all product-specific discounts |

  | total_discount_amount | `total_discount_amount` = `discount_amount` +
  `items_discount_amount` | This field sums up all order-level and all
  product-specific discounts |

  | applied_discount_amount | N/A | This field shows the order-level discount
  applied in a particular request |

  | items_applied_discount_amount | sum(items, i => i.applied_discount_amount) |
  This field sums up all product-specific discounts applied in a particular
  request |

  | total_applied_discount_amount | `total_applied_discount_amount` =
  `applied_discount_amount` + `items_applied_discount_amount` | This field sums
  up all order-level and all product-specific discounts applied in a particular
  request |


  <!-- theme: info -->

  > 📘 Rollbacks

  >

  > You can't roll back a child redemption. When you call rollback on a stacked
  redemption, all child redemptions will be rolled back. You need to refer to a
  parent redemption ID in your <!-- [rollback
  request](OpenAPI.json/paths/~1redemptions~1{parentRedemptionId}~1rollbacks/post)
  -->[rollback request](ref:rollback-stacked-redemptions).
api:
  file: voucherify-api.json
  operationId: post-redemptions-client_side
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---