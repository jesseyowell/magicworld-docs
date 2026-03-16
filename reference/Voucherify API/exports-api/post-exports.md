---
title: Create Export
excerpt: >-
  Create export object. The export can be any of the following types: `voucher`,
  `redemption`, `publication`, `customer`, `order`, or `points_expiration`.  


  ## Defaults


  If you only specify the object type in the request body without specifying the
  fields, the API will return the following fields per export object:


  | **Export Object** | **Default fields returned** |

  |:---|:---|

  | order | `id`, `source_id`, `status` |

  | voucher | `code`, `voucher_type`, `value`, `discount_type` |

  | publication | `code`, `customer_id`, `date`, `channel` |

  | redemption | `id`, `object`, `voucher_code`, `customer_id`, `date`, `result`
  |

  | customer | `name`, `source_id` |

  | points_expiration | `id`, `campaign_id`, `voucher_id`, `status`,
  `expires_at`, `points` |



  ## Fetching particular data sets


  Using the `parameters` body parameter, you can narrow down which fields to
  export and how to filter the results. The fields are an array of strings
  containing the data that you would like to export. These fields define the
  headers in the CSV file. The array can be a combintation of any of the
  following available fields:


  ## Orders  


  | **Field** | **Definition** | **Example Export** |

  |:---|:---|:---|

  | id | Unique order ID. | ord_A69RIxEdRsPuC6i8gFGVHUft |

  | source_id | Unique order source ID. | 8638 |

  | created_at | Timestamp in ISO 8601 format representing the date and time
  when the order was created. | 2022-03-09T09:16:32.521Z |

  | updated_at | Timestamp in ISO 8601 format representing the date and time
  when the order was last updated. | 2022-03-09T09:16:33.331Z |

  | status | Order status. | `PAID`, `CREATED`, `FULFILLED`, `CANCELED` |

  | amount | Total amount of order items. | 7700 |

  | discount_amount | Represents total amount of the discount applied to whole
  cart. | 500 |

  | items_discount_amount | Represents total amount of the discount applied to
  order line items. | 100 |

  | total_discount_amount | All discounts applied to the order including
  discounts applied to particular order line items and discounts applied to the
  whole cart. | 600 |

  | total_amount | Total order amount after applying all discounts. | 7100 |

  | customer_id | Customer unique ID. | cust_2G4fUQdCXUqp35nXNleav7bO |

  | referrer_id | Referrer unique ID. | cust_IkrTR674vvQvr9a4rDMiqglY |

  | metadata | Order metadata; expressed as metadata.X, where X is the name of
  the custom metadata property. | 1 |


  ## Vouchers  


  | **Field** | **Definition** | **Example Export** |

  |:---|:---|:---|

  | id | Unique voucher ID. | v_HSnGD2vNIHYighTQxwcB4dtVAv8VOmZD |

  | code | Unique voucher code. | WELCOME100 |

  | voucher_type | Type of voucher. | `DISCOUNT_VOUCHER`, `GIFT_VOUCHER`,
  `LOYALTY_CARD` |

  | value | Value of voucher. | `DISCOUNT_VOUCHER` : amount, percent,
  unit<br>`GIFT_VOUCHER`: amount left to spend<br>`LOYALTY_CARD`: available
  usable points |

  | discount_type | The type of discount for a `DISCOUNT_VOUCHER`. | `AMOUNT`,
  `PERCENT`, `UNIT`, `FIXED` |

  | campaign | Unique campaign name. | Summer Discounts 20% off |

  | category | Tag defining the category that this voucher belongs to. |  |

  | start_date | Start date defines when the code starts to be active.
  Activation timestamp in ISO 8601 format. Voucher is _inactive_ before this
  date. | 2020-12-10T23:00:00.000Z |

  | expiration_date | Expiration date defines when the code expires. Expiration
  timestamp in ISO 8601 format. Voucher is _inactive_ after this date. |
  2023-12-31T23:00:00.000Z |

  | gift_balance | Amount left to spend. | 1000 |

  | loyalty_balance | Available usable points. | 2000 |

  | redemption_quantity | Maximum number of times a voucher can be redeemed. | 2
  |

  | redemption_count | Total redemptions. | 59 |

  | active | Boolean indicating whether the voucher is available for use. |
  `true`, `false` |

  | qr_code | URL to QR representation of encrypted code. |  |

  | bar_code | URL to barcode representation of encrypted code. |  |

  | metadata | Custom voucher metadata. |  |

  | is_referral_code | Boolean indicating whether the voucher is a referral
  code. | `true`, `false` |

  | created_at | Timestamp in ISO 8601 format representing the date and time
  when the voucher was created. | 2022-04-14T09:55:46.814Z |

  | updated_at | Timestamp in ISO 8601 format representing the date and time
  when the voucher was last updated. | 2022-04-14T10:02:18.036Z |

  | validity_timeframe_interval | Defines the intervening time between two time
  points in ISO 8601 format, expressed as a duration. For example, a voucher
  with an interval of `P2D` will be active every other day. | P2D |

  | validity_timeframe_duration | Defines the amount of time the voucher will be
  active in ISO 8601 format. For example, a voucher with a duration of `PT1H`
  will be valid for a duration of one hour. | PT1H |

  | validity_day_of_week | Array corresponding to the particular days of the
  week in which the voucher is valid. | "1,2,3,4,5" |

  | discount_amount_limit | For `PERCENT` discount type, this is the maximum
  threshold allowed to be deducted. | 50 |

  | campaign_id | Parent campaign ID. | camp_7s3uXI44aKfIk5IhmeOPr6ic |

  | additional_info | An optional field to keep any extra textual information
  about the code such as a code description and details. |  |

  | customer_id | Unique customer ID of the assigned owner to whom the voucher
  was published. | cust_7iUa6ICKyU6gH40dBU25kQU1 |

  | discount_unit_type | For `UNIT` discount type, either a shipping or product
  ID for a `UNIT` discount with one product. | prod_5h1pp1ng,
  prod_0a9f9aeddb019a42db |

  | discount_unit_effect | `UNIT` discount effect. | `ADD_MANY_ITEMS`,
  `ADD_MISSING_ITEMS`,`ADD_NEW_ITEMS` |

  | customer_source_id | Unique customer source id of the assigned owner to whom
  the voucher was published. | name.lastname@email.com |



  ## Publications


  | **Field** | **Definition** | **Example Export** |

  |:---|:---|:---|

  | voucher_code | Unique voucher code. | WELCOME100 |

  | customer_id | Customer unique ID. | cust_7iUa6ICKyU6gH40dBU25kQU1 |

  | customer_source_id | Unique customer source id of the assigned owner to whom
  the voucher was published. | name.lastname@email.com |

  | date | Timestamp in ISO 8601 format representing the date and time when the
  voucher was published. | 2022-04-28T10:19:30.792Z |

  | channel | Publication channel. | voucherify-website |

  | campaign | Unique campaign name. | Summer Discounts 20% off |

  | is_winner |  |  |

  | metadata | Custom publication metadata. |  |


  ## Redemptions


  | **Field** | **Definition** | **Example Export** |

  |:---|:---|:---|

  | id | Unique redemption ID. | r_0acf3a6dae00e679c8, rf_0acf3a495740e679b8 |

  | object | Object being exported; by default `redemption`. | redemption |

  | date | Timestamp in ISO 8601 format representing the date and time when the
  voucher was redeemed. | 2022-03-23T08:52:24.867Z |

  | voucher_code | Unique voucher code redeemed. | WELCOME100 |

  | campaign | Parent campaign name of voucher if applicable. | Summer Discounts
  20% off |

  | promotion_tier_id |  | promo_Mwy9XpA0TLctSGriM5kum0qp |

  | customer_id | Unique customer ID of redeeming customer. |
  cust_nk0N1uNQ1YnupAoJGOgvsODC |

  | customer_source_id | Unique source ID of redeeming customer. |
  name.lastname@email.com |

  | customer_name | Customer name. | John Smith |

  | tracking_id |  | track_Pw6r3ejnml43kIwNS4Zj09KZ67xOfLUy |

  | order_amount | Total order amount before applying all discounts. | 1000 |

  | gift_amount | Gift credits used for redemption. | 10 |

  | loyalty_points |  | 12 |

  | result | Tells you whether the redemption succeeded. | `SUCCESS`, `FAILURE`
  |

  | failure_code | Internal Voucherify code for reason why redemption failed. |
  invalid_customer |

  | failure_message | A human-readable message providing a short description
  explaining why the redemption failed. | Customer must be a holder of a loyalty
  card. |

  | metadata | Custom redemption metadata. |  |


  ## Customers


  | **Field** | **Definition** | **Example Export** |

  |:---|:---|:---|

  | name | Customer name. | John Smith |

  | id | Unique customer ID. | cust_J1CDUdbqn5Exva8ASWk1Fq0j |

  | description | An arbitrary string that you can attach to a customer object.
  | Customer requesting to be added to VIP tier. |

  | email | Customer's email. | name.lastname@email.com |

  | source_id | Unique custom customer identifier. | name.lastname@email.com |

  | created_at | Timestamp in ISO 8601 format representing the date and time
  when the customer was created. | 2022-02-03T13:10:11.928Z |

  | address_city | City | Houston |

  | address_state | State | TX |

  | address_line_1 | First line of customer's address. | 72738 Main St |

  | address_line_2 | Second line of customer's address. | Bld 2, Apt 4 |

  | address_country | Country | United States of America |

  | address_postal_code | Postal code (ZIP code) | 77042-4143 |

  | redemptions_total_redeemed | Total customer redemptions. | 5 |

  | redemptions_total_failed | Total customer failed redemptions. | 2 |

  | redemptions_total_succeeded | Total customer succeeded redemptions. | 3 |

  | redemptions_total_rolled_back | Total customer redemptions that were rolled
  back. | 3 |

  | redemptions_total_rollback_failed | Total customer redemptions that were
  unsuccessfully rolled back. | 2 |

  | redemptions_total_rollback_succeeded | Total customer redemptions that were
  successfully rolled back. | 1 |

  | orders_total_amount | Total sum of order amounts over customer lifetime.
  Value is multiplied by 100 to precisely represent 2 decimal places. | 10000
  (represents $100) |

  | orders_total_count | Total number of customer orders. Value is multiplied by
  100 to precisely represent 2 decimal places. | 2 |

  | orders_average_amount | Average amount spent on orders. Value is multiplied
  by 100 to precisely represent 2 decimal places. | 50 |

  | orders_last_order_amount | How much did the customer spend on their last
  order. Value is multiplied by 100 to precisely represent 2 decimal places. |
  50 |

  | orders_last_order_date | When was the last customer order; timestamp in ISO
  8601 format representing the date and time. | 2022-02-03T13:17:30.630Z |

  | loyalty_points | Sum of customer's loyalty points to go across all loyalty
  cards. | 2000 |

  | loyalty_referred_customers | How many customers were referred by this
  customer. | 3 |

  | updated_at | Timestamp in ISO 8601 format representing the date and time
  when the customer was updated. | 2022-02-14T14:10:14.305Z |

  | phone | Customer's phone number. | +1 (294) 752-1846 |

  | birthday | Customer's birthday. | 2022-01-01 |

  | metadata | Customer metadata. | All metadata fields defined in Metadata
  Schema for the Customer object. |

  | birthdate | Customer's birthdate. | 2022-01-01 |


  ## Points Expirations


  | **Field** | **Definition** | **Example Export** |

  |:---|:---|:---|

  | id | Loyalty points bucket ID. | lopb_Wl1o3EjJIHSNjvO5BDLy4z1n |

  | campaign_id | Campaign ID of the parent loyalty campaign. |
  camp_7s3uXI44aKfIk5IhmeOPr6ic |

  | voucher_id | Voucher ID of the parent loyalty card. |
  v_YLn0WVWXSXbUfDvxgrgUbtfJ3SQIY655 |

  | status | Status of the loyalty points bucket. | `ACTIVE` or `INACTIVE` |

  | expires_at | Timestamp in ISO 8601 format representing the date when the
  points expire. | 2022-06-30 |

  | points | Number of points. | 1000 |
api:
  file: voucherify-api.json
  operationId: post-exports
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---