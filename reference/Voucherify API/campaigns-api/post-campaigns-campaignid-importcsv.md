---
title: Import Vouchers to Campaign by CSV
excerpt: >-
  Imports vouchers to an **existing** campaign.  



  The CSV file has to include headers in the first line. 


  Curl Example

  <!--

  title: "Example Request"

  lineNumbers: true

  -->

  ```cURL

  curl -X POST \
    https://api.voucherify.io/v1/campaigns/TEST-CAMPAIGN/importCSV \
    -F file=@/path/to/campaigns.csv \
    -H "X-App-Id: c70a6f00-cf91-4756-9df5-47628850002b" \
    -H "X-App-Token: 3266b9f8-e246-4f79-bdf0-833929b1380c"
  ```


  You can import values for the following fields: `Code` (**required**),
  `Category`, `Active`. In a gift cards import, you can also include the current
  card balance using the `Gift Amount` header. In a loyalty cards import, you
  can also include the current loyalty card score in points using the `Loyalty
  Points` header. Remaining CSV columns will be mapped to metadata properties. 


  Discount type, time limits, and validation rules will be taken from the <!--
  [campaign object](OpenAPI.json/components/schemas/2_obj_campaign_object)
  -->[campaign object](ref:get-campaign) settings. 



  | **Active** | **Code** | **Loyalty Points** | **Gift Amount** | **Category**
  | **Custom_metadata_property** |

  |---|---|---|---|---|---|

  | Use `true` or `false` to enable or disable the voucher; this flag can be
  used to turn off the ability to redeem a voucher even though it is within the
  campaign's start/end validity timeframe. | The unique voucher code. | The
  number of points to be added to the loyalty card. If you leave this undefined,
  then the initial number of points will be set according to the campaign
  settings.<br>Context: `LOYALTY_PROGRAM` | The initial gift card
  balance.<br>Context: `GIFT_VOUCHERS` | A custom tag for the voucher to help
  you filter codes; you can either import the category name or a unique
  Voucherify-assigned category ID. | Any additional data that you would like to
  store for the given loyalty card as a Custom attribute. Remember to define the
  metadata schema in the Dashboard prior to importing codes. |

  |<!-- theme: info -->


  > 📘 Active

  >

  > The CSV file is allowed in two versions; either with or without a column
  titled `Active`. It indicates whether the voucher is enabled after the import
  event.  


  This API request starts a process that affects Voucherify data in bulk. 


  In case of small jobs (like bulk update) the request is put into a queue and
  processed once every other bulk request placed in the queue prior to this
  request is finished. However, when the job takes a longer time (like vouchers
  generation) then it is processed in small portions in a round-robin fasion.
  When there is a list of vouchers generation scheduled, then they will all have
  the `IN_PROGRESS` status shortly. This way, small jobs added just after
  scheduling big jobs of the same type will be processed in a short time
  window. 


  The result will return the async ID. You can verify the status of your request
  via this [API request](ref:get-async-action).
api:
  file: voucherify-api.json
  operationId: post-campaigns-campaignId-importCSV
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---