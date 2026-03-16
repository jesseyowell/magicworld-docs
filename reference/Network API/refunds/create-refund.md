---
title: Create refund
excerpt: |-
  Creates a refund from a merchant to a customer.

  You can create 2 types of refunds: **linked**, which are associated with a
  payment, and **unlinked**, which are not associated with a payment:

  - To issue a linked refund, provide a `payment_id` in the request.
  - To issue an unlinked refund, provide a `grant_id` in the request. The grant
  must be associated with the `ON_FILE_PAYMENT` or `UNLINKED_REFUND` actions.
  To generate a grant to pass to this field, use the Customer Request API.

  **This endpoint is not rate limited.**

  Scopes: `REFUNDS_WRITE`
api:
  file: network-api.json
  operationId: create-refund
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---