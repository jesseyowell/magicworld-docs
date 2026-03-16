---
title: Examine Qualification
excerpt: >-
  Display vouchers qualified to the given customer and context (e.g., order,
  loyalty reward). Checks up to 50 **standalone vouchers**. 


  > 👍 Prevailing assumption

  > You data is synced with Voucherify.

   ## How does this endpoint work? 

   A property's value that does not meet a validation rule requirement will disqualify that particular voucher and it will not be listed in the results.

  As a sample use case, you can imagine a requirement of displaying coupons
  available for the customer below the shopping cart. The customer can choose
  and apply the proposed voucher.

   ## What's excluded? 

   The verification logic won't run against _coupons from bulk unique code campaigns_. For campaigns with multiple unique codes, you should run a <!-- [dedicated function](OpenAPI.json/paths/~1campaigns~1qualification/post) -->[dedicated function](ref:examine-campaigns-qualification) for searching and identifying qualified campaigns.

   ## Customizing the response<!-- theme: info -->

  > 📘 Query parameters let you sort and filter the returned vouchers

  >

  > Customize your response:

  > - If you only care about verifying a customer, use `audienceRulesOnly` set
  to `true`. 

  >- If you want to limit the number of vouchers to be returned from the entire
  pool of eligible vouchers, set a `limit`. This will return vouchers sorted by
  `-created_at`, by default beginning with the most recent vouchers listed at
  the top.

  > - If you have a preference on the sorting order of the returned vouchers,
  you can use `order` to customize your response.

   ## Sending the request body payload
  <!--

  type: tab


  title: Customer

  -->

   ## Customer

  You have the option of sending customer data via the dedicated `customer`
  object in the request body or a nested `customer` object within the `order`
  object.
   ### Available options:

   - You can either pass a customer `id` (Voucherify system generated),

   - a `source_id` (your own unique internal customer identifier e.g., email, database ID, CRM id), 

   - a combination of the remaining parameters in the customer object, 

   - a combination of customer `id` and remaining parameters excluding `source_id`, or

   - a combination of `source_id` and remaining parameters excluding `id`

   #### Note:

   For the latter two options, if you pass the `source_id` or the `id` with the other parameters, the logic will run independently for parameters explicitly passed in the request body versus those not explicitly passed in the request body. For _parameters not explicitly listed in the payload_, the verification will be against the data stored for that customer in the system. On the otherhand, for any _parameter values explicitly passed in the payload_, the logic will ignore those stored in the system and will use the new values provided in the qualification request body. 

   The qualification runs against rules that are defined through the <!-- [Create Validation Rules](https://docs.voucherify.io/reference/create-validation-rules) -->[Create Validation Rules](ref:create-validation-rules) endpoint or via the Dashboard. [Read more](https://support.voucherify.io/article/148-how-to-build-a-rule). 

  ## Order

    ### Available options:

   - You can either pass an order `id` (Voucherify system generated),

   - a `source_id` (your own unique internal order identifier), 

   - a combination of the remaining parameters in the order object, 

   - a combination of order `id` and remaining parameters excluding `source_id`, or

   - a combination of `source_id` and remaining parameters excluding `id`

   #### Note:

   For the latter two options, if you pass the `source_id` or the `id` with the other parameters, the logic will run independently for parameters explicitly passed in the request body versus those not explicitly passed in the request body. For _parameters not explicitly listed in the payload_, the verification will be against the data stored for that order in the system. On the otherhand, for any _parameter values explicitly passed in the payload_, the logic will ignore those stored in the system and will use the new values provided in the qualification request body. 

   The qualification runs against rules that are defined through the <!-- [Create Validation Rules](https://docs.voucherify.io/reference/create-validation-rules) -->[Create Validation Rules](ref:create-validation-rules) endpoint or via the Dashboard. [Read more](https://support.voucherify.io/article/148-how-to-build-a-rule).

  ## Guidelines:


  To validate against vouchers with total order `amount` requirements, make sure
  to include the total order `amount` in the order object or alternatively the
  `amount` for _every_ order item (the application will then add each amount to
  get the total and perform the qualification checks). If the total order
  `amount` is provided along with the individual items' amounts, the total order
  `amount` will take precedence.


  <!-- title: Payload configuration -->

  | **Case** | **Order-Level Parameter Included** | **Item-Level Parameter
  Included** | **Precedence** | **Calculation Result** | **Parameter included in
  payload accounts for checks against requirements in these validation rules** |

  |:---:|:---:|:---:|:---:|---|---|

  | **1** | `amount` | `amount` | Order-level | Uses order-level `amount` | -
  Total order amount |

  | **2** |  | `amount` | Item-level | Sums each item-level `amount` | - Total
  order amount  <br>- subtotal of matched items |

  | **3** |  | `price`<br>`quantity` | Item-level | Multiplies each item's
  (`price` x `quantity`) to get item `amount` and then adds each item's `amount`
  to get total order `amount`  | - Total order amount<br>- Subtotal of matched
  items<br>- Unit price of any matching order line<br>- Price of each item/Price
  of any item |

  | **4** |  | `amount`  <br>`price`    <br>`quantity` | Item-level `amount` |
  Uses item-level `amount` for  total order `amount` calculation, ignores
  (`price` x `quantity`) calculation | - Total order amount (uses item `amount`
  if provided or `price` x `quantity` for items without `amount` property;
  `amount` takes precedence in case all 3 properties are provided for an
  item)<br>- Subtotal of matched items (uses item `amount`, takes precedence if
  all 3 properties are provided)<br>- Unit price of any matching order line<br>-
  Price of each item/Price of any item |

  | **5** | `amount` | `amount`  <br>`price`  <br>`quantity` | Order-level  |
  Uses order-level `amount` for total order `amount` | - Total order amount
  (uses order-level `amount`). <br>- Subtotal of matched items (see case **4**
  for details). <br>- Unit price of any matching order line  <br>- Price of each
  item/Price of any item |
    

  ## Reward

   ## Gift Card
api:
  file: voucherify-api.json
  operationId: post-vouchers-qualification
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---