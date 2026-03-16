---
title: Validate Promotions
excerpt: >-
  Use this method to get valid promotions for a given customer and order.


  ### Advanced validation filters


  You can narrow down a validation to a specific promotion ID or tier metadata.
  Here are the examples of filtering queries you can use:


  | **Filter** | **Example** |

  |:---|:---|

  | promotion_id | [filters][promotion_id][conditions][$is]={{campaign_id}} |

  | tier metadata | [filters][metadata.{{promotion tier metadata
  key}}][conditions][$is]={{promotion tier metadata value}} |


  <!--

  title: "Validate promotion against customer rules"

  lineNumbers: true

  -->

  ```cURL

  curl -X GET \
    -H "X-Client-Application-Id: 011240bf-d5fc-4ef1-9e82-11eb68c43bf5" \
    -H "X-Client-Token: 9e2230c5-71fb-460a-91c6-fbee64707a20" \
    -H "Content-Type: application/json" \
    -d '{
      "customer": {
          "id": "cust_gN9KgORZECfdhG9qT6n82Zr7"
      },
      "order": {
          "items": [
              {
                  "product_id": "prod_0a9f9ab4ab019a42d5",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0a9f9aeddb019a42db",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0a9f9ab4ab019a42d5",
                  "quantity": "1"
              },
              {
                  "sku_id": "sku_0b7d7dfb090be5c619",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0b72b0bd64d198e3ae",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0b7d7c4e814be5c502",
                  "quantity": 1
              }
          ],
          "metadata":{
              "payment_mean": ["credit-card"]
          }
      },
      "options": {
          "expand": [
              "category"
          ]
      }
    }'/
    'https://api.voucherify.io/v1/promotions/validation?audienceRulesOnly=true'
  ```

  <!--

  title: "Validate promotion for specific campaign"

  lineNumbers: true

  -->

  ```cURL

  curl -X GET \
    -H "X-Client-Application-Id: 011240bf-d5fc-4ef1-9e82-11eb68c43bf5" \
    -H "X-Client-Token: 9e2230c5-71fb-460a-91c6-fbee64707a20" \
    -H "Content-Type: application/json" \
    -d `{
      "customer": {
          "id": "cust_gN9KgORZECfdhG9qT6n82Zr7"
      },
      "order": {
          "items": [
              {
                  "product_id": "prod_0a9f9ab4ab019a42d5",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0a9f9aeddb019a42db",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0a9f9ab4ab019a42d5",
                  "quantity": "1"
              },
              {
                  "sku_id": "sku_0b7d7dfb090be5c619",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0b72b0bd64d198e3ae",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0b7d7c4e814be5c502",
                  "quantity": 1
              }
          ],
          "metadata":{
              "payment_mean": ["credit-card"]
          }
      },
      "options": {
          "expand": [
              "category"
          ]
      },
      "metadata": {
          "store_names": "Store 1 - New York - Broadway"
      }
    }`\
    'https://api.voucherify.io/v1/promotions/validation?[filters][promotion_id][conditions][$is]=camp_nYcAyjFXmEaBU0nB7EQ4hVTr'
  ```

  <!--

  title: "Validate promotion based on tier metadata"

  lineNumbers: true

  -->

  ```cURL

  curl -X GET \
    -H "X-Client-Application-Id: 011240bf-d5fc-4ef1-9e82-11eb68c43bf5" \
    -H "X-Client-Token: 9e2230c5-71fb-460a-91c6-fbee64707a20" \
    -H "Content-Type: application/json" \
    -d `{
      "customer": {
          "id": "cust_gN9KgORZECfdhG9qT6n82Zr7"
      },
      "order": {
          "items": [
              {
                  "product_id": "prod_0a9f9ab4ab019a42d5",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0a9f9aeddb019a42db",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0a9f9ab4ab019a42d5",
                  "quantity": "1"
              },
              {
                  "sku_id": "sku_0b7d7dfb090be5c619",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0b72b0bd64d198e3ae",
                  "quantity": 1
              },
              {
                  "product_id": "prod_0b7d7c4e814be5c502",
                  "quantity": 1
              }
          ],
          "metadata":{
              "payment_mean": ["credit-card"]
          }
      },
      "options": {
          "expand": [
              "category"
          ]
      }
    }`\
    'https://api.voucherify.io/v1/promotions/validation?[filters][metadata.has_budget][conditions][$is]=true'
  ```
api:
  file: voucherify-api.json
  operationId: post-promotions-validation
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---