---
title: Validate Voucher (client-side)
excerpt: >-
  To verify a voucher code given by customer, you can use this method. It is
  designed for client side integration which means that is accessible only
  through public keys. This method is designed to be run directly either in web
  browsers or mobile apps.


  <!-- theme: danger -->

  > ❗️ Important  

  >

  > This endpoint supports the validation of a single promo code. If you need to
  validate more than one incentive, you can use the <!-- [Stackable discounts
  API](OpenAPI.json/paths/~1validations/post) -->[Stackable discounts
  API](ref:validate-stacked-discounts). The stacking discounts API lets you
  validate up to 5 incentives per call. Before integrating Voucherify, choose
  which validation endpoint you prefer to use.


  <!-- theme: info -->


  > ❗️ Specifying gift credits and loyalty points

  >

  > This endpoint does not support specifying the specific amount of gift
  credits to apply to an order nor the specific amount of loyalty points to an
  order. It calculates the amount that is available on the card and applies as
  much credits or points as possible to cover the total amount. 


  ### Set customer identity (optional)


  Voucherify can help you track anonymous customers. Once you integrate
  Voucherify into your web app and call the validate method, Voucherify will
  return a tracking ID and the script will store it in a cookie. Each subsequent
  validate call will use the same tracking ID.


  Voucherify tracks a user using a tracking ID to see if the user who is
  validating vouchers is the same as the one who consuming them. Voucherify does
  this by setting up an identity for the user. A `tracking_id` will be generated
  on the server side, unless you specify your own `tracking_id`. In both cases,
  you will receive the `tracking_id` in the validation response.


  The returned `tracking_id` field should be used as the customer `source_id` in
  subsequent redemption requests. Moreover, the `tracking_id` returned from
  Validation API is encoded. Voucherify will recognize both values for
  identifying customer - the one before encryption sent as a query parameter to
  the **GET** `/validate` request, and the version encrypted and returned as
  part of the validation request.


  ### Sample workflow


  Customer tracking workflow in a nutshell:


  **Client-side:**
    * A customer visits your website.
    * A customer validates a voucher code. That triggers a validate request to be sent to Voucherify. In the request, you pass the tracking_id or customer.source_id. As a result, the API call to this endpoint returns an **encoded** `tracking_id`.

  **Backend:**
    * Once the customer finishes the checkout process, your website passes the `tracking_id` to your backend during a redemption call. The `tracking_id` is sent as a value assigned to the property *source_id* in a customer object.
    * A customer object is created and within the redemption response, you get a customer `id`.
    * You can use the customer `id` or the customer `source_id` to fetch or modify the customer details.
    
  A customer is created (upserted) automatically with a redemption call.
  Alternatively, you can create a new profile by creating a customer via a
  dedicated API method. Take a look at the customer object to understand the
  <!-- [entity's
  structure](OpenAPI.json/components/schemas/9_obj_customer_object) -->[entity's
  structure](ref:get-customer). 


  <!-- theme: info -->


  > 📘 Customer identifier

  >

  > The source id of the customer may either be an already hashed version of the
  `tracking_id`, which you received in a response from a validation request or a
  custom ID you predefined (i.e. an email address). Nevertheless, we recommend
  using identifiers delivered by Voucherify API.


  <!--

  title: "Validate Discount Voucher"

  lineNumbers: true

  -->

  ```cURL

  curl -X GET \
    -H "X-Client-Application-Id: 011240bf-d5fc-4ef1-9e82-11eb68c43bf5" \
    -H "X-Client-Token: 9e2230c5-71fb-460a-91c6-fbee64707a20" \
    -H "Content-Type: application/json" \
    -H "origin: yourdomain.com" \
    'https://api.voucherify.io/client/v1/validate?code=PAYINEUROS&session_type=LOCK&session_key=A&session_ttl=1&session_ttl_unit=NANOSECONDS&customer=cust_4vMj8Twr5nBzvTrNCgipMb6M&[order][metadata][currency]=EUR&[metadata][location_id][0]=L1&[item][0][source_id]=webinar_BF_sweater_pink_sweater&[item][0][quantity]=2&[item][0][related_object]=product'
  ```

  <!--

  title: "Validate Loyalty Card"

  lineNumbers: true

  -->

  ```cURL

  curl -X GET \
    -H "X-Client-Application-Id: 011240bf-d5fc-4ef1-9e82-11eb68c43bf5" \
    -H "X-Client-Token: 9e2230c5-71fb-460a-91c6-fbee64707a20" \
    -H "Content-Type: application/json" \
    -H "origin: yourdomain.com" \
    'https://api.voucherify.io/client/v1/validate?code=LOYALTY-CARD-ng3Kb9tM&session_type=LOCK&session_key=A&session_ttl=1&session_ttl_unit=NANOSECONDS&customer[source_id]=286401dc-6f4c-4ebb-8ca2-9f78b3e84c7d&[order][metadata][currency]=EUR&[customer][metadata][age]=24&[customer][metadata][acquisition_channel]=Facebook&[metadata][location_id][0]=L1&[item][0][source_id]=webinar_BF_sweater_pink_sweater&[item][0][quantity]=2&[item][0][related_object]=product&[item][1][source_id]=webinar_BF_pants_gray_sweat_pants&[item][1][quantity]=2&[item][1][related_object]=product&[item][2][product_id]=prod_0bd76bb4aa003890cb&[item][2][quantity]=2&[item][3][source_id]=M0E20000000ELDH&[item][3][quantity]=3&[item][3][related_object]=sku'
  ```

  <!--

  title: "Validate Gift Card"

  lineNumbers: true

  -->

  ```cURL

  curl -X GET \
    -H "X-Client-Application-Id: 011240bf-d5fc-4ef1-9e82-11eb68c43bf5" \
    -H "X-Client-Token: 9e2230c5-71fb-460a-91c6-fbee64707a20" \
    -H "Content-Type: application/json" \
    -H "origin: yourdomain.com" \
    'https://api.voucherify.io/client/v1/validate?code=GIFT-CARD-kW4aEsfB&session_type=LOCK&session_key=A&session_ttl=1&session_ttl_unit=NANOSECONDS&customer[source_id]=286401dc-6f4c-4ebb-8ca2-9f78b3e84c7d&[order][metadata][currency]=EUR&[customer][metadata][age]=24&[customer][metadata][acquisition_channel]=Facebook&[metadata][location_id][0]=L1&[item][0][source_id]=webinar_BF_sweater_pink_sweater&[item][0][quantity]=2&[item][0][related_object]=product&[item][1][source_id]=webinar_BF_pants_gray_sweat_pants&[item][1][quantity]=2&[item][1][related_object]=product&[item][2][product_id]=prod_0bd76bb4aa003890cb&[item][2][quantity]=2&[item][3][source_id]=M0E20000000ELDH&[item][3][quantity]=3&[item][3][related_object]=sku&[item][4][sku_id]=sku_0b661e41fc0d35a8f1&[item][4][quantity]=4'
  ```

  <!--

  title: "Validate Referral Card"

  lineNumbers: true

  -->

  ```cURL

  curl -X GET \
    -H "X-Client-Application-Id: 011240bf-d5fc-4ef1-9e82-11eb68c43bf5" \
    -H "X-Client-Token: 9e2230c5-71fb-460a-91c6-fbee64707a20" \
    -H "Content-Type: application/json" \
    -H "origin: yourdomain.com" \
    'https://api.voucherify.io/client/v1/validate?code=REFERRAL-CODE-OxBakPYf&amount=10000'
  ```


  ### [JSFiddle Example](https://jsfiddle.net/voucherify/gfu2bgn5/)

  <!--

  title: "Example Code - Voucherify.js"

  lineNumbers: true

  -->

  ```javascript

  <script type="text/javascript"
  src="https://cdn.rawgit.com/rspective/voucherify.js/v1.4.5/dist/voucherify-1.4.5.js"></script>


  <script type="text/javascript">
    function init() {
      Voucherify.initialize(
        "011240bf-d5fc-4ef1-9e82-11eb68c43bf5", //YOUR-CLIENT-APPLICATION-ID-FROM-SETTINGS
        "9e2230c5-71fb-460a-91c6-fbee64707a20" //YOUR-CLIENT-TOKEN-FROM-SETTINGS
      );
    };
    init();
    
    //-- [Optional] If you want us to track your customers' activity, then you should invoke the following function to set identity. You have to do it only once. If the identity parameter is not passed, then we will generate it for you.
    Voucherify.setIdentity("your-customer-uniq-id");
    Voucherify.validate("Testing7fjWdr", function callback (response) {
      console.log(response);
    });
  </script>

  ```


  ### Examples with Query Parameters


  | **Query Parameters** | **Example URL** |

  |:---|:---|

  | Shortcut - `customer` query param instead of `customer[source_id]` |
  `https://api.voucherify.io/client/v1/validate?code=sKKFCKLZ&amount=10100&customer=customer_id`
  |

  | Pass `customer`'s and `redemption`'s context `metadata` in query parameters
  |
  `https://api.voucherify.io/client/v1/validate?code=sKKFCKLZ&amount=10100&customer=sure_he_is_new&metadata[shop]=1&customer[metadata][propsy]=2&metadata[test]=true`
  |

  | Use `tracking_id` instead of `source_id` |
  `https://api.voucherify.io/client/v1/validate?code=IKU-mvS-JOG&amount=10100&tracking_id=sure_he_is_new_5&metadata[shop]=1&metadata[test]=true`
  |


  ### Reasons why a validation might fail


  Voucher validation might fail because of one of these reasons:


  * `voucher not found` - voucher doesn't exist or was <!--
  [deleted](OpenAPI.json/paths/~1vouchers~1{code}/delete)
  -->[deleted](ref:delete-voucher)

  * `voucher expired` - voucher is out of [start date - expiration date]
  timeframe

  * `voucher is disabled` - learn more about <!-- [disabled
  vouchers](OpenAPI.json/paths/~1vouchers~1{code}~1disable) -->[disabled
  vouchers](ref:disable-voucher)

  * `customer does not match segment rules` - learn more customer tracking LINK

  * `order does not match validation rules` - learn more about validation rules
  LINK
api:
  file: voucherify-api.json
  operationId: get-validate
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---