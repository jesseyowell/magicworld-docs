---
title: Import Orders
excerpt: >-
  <!-- theme: info -->


  > 🚧 Historical orders

  >

  > This endpoint should only be used to import historical orders into
  Voucherify. For on-going synchronization, the <!-- [create
  order](OpenAPI.json/paths/~1orders/post) -->[create order](ref:create-order)
  and <!-- [update order](OpenAPI.json/paths/~1orders~1{orderId}/put) -->[update
  order](ref:update-order) endpoints should be used. This is critical because
  this endpoint does not store events or launch distributions.


  ## Limitations


  ### Import volume


  There can be only a single on-going order import per tenant per project at a
  given time. The user can schedule more imports but those extra imports will be
  scheduled to run in sequence one by one.  


  ### Maximum count of orders in single import


  There is a `2000` limit but we might decide to change it to a lower / higher
  value at any given time depending if we find this value is too high or too low
  with time.


  ## Notifications


  There are no notifications on the Dashboard because this import is launched
  via the API.


  ## Triggered actions
    
  If you import orders with customers, then a logic will be scheduled
  responsible for placing these customers into segments and refreshing the
  segment's summary. Consequently, this update will trigger 

  - **customers entering into segments** 

  - **distributions** based on any rules tied to customer entering segment(s)

  - **earning rules** based on the customer entering segment(s)


  ## What is not triggered


  1. No webhooks are triggered during the import of orders - for both orders and
  upserted products / skus.  


  2. Distributions based on Order Update, Order Paid, Order Created and Order
  Cancelled. In other words if you have a distribution based on Order Paid and
  you import an order with a PAID status, the distribution is not going to be
  triggered.    


  3. No events are created during the import of orders - for both orders and
  upserted products / skus. In other words you won't see any events in the
  Activity tab in the Dashboard such as Order created or Order paid. If you are
  additionally upserting products / skus, then you won't see the Product created
  events listed, etc.   


  4. Earning rules based on Order Paid won't be triggered.


  This API request starts a process that affects Voucherify data in bulk. 


  In case of small jobs (like bulk update) the request is put into a queue and
  processed once every other bulk request placed in the queue prior to this
  request is finished. However, when the job takes a longer time (like vouchers
  generation) then it is processed in small portions in a round-robin fasion.
  When there is a list of vouchers generation scheduled, then they will all have
  the IN_PROGRESS status shortly. This way, small jobs added just after
  scheduling big jobs of the same type will be processed in a short time
  window. 


  The result will return the async ID. You can verify the status of your request
  via this [API request](ref:get-async-action).
api:
  file: voucherify-api.json
  operationId: post-orders-import
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---