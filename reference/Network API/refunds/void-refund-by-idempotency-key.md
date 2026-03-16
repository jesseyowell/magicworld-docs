---
title: Void refund by idempotency key
excerpt: >-
  Moves an authorized refund to the voided state using the idempotency key
  specified while creating the refund.


  > **Note**: You can only void an authorized refund. If a refund is captured,
  there is no way to reverse it.


  In rare cases, an issue with an integration, network connectivity, or the Cash
  App Pay API may cause an API client to end up in a state where a refund is
  created in Cash App Pay, but the API client doesn't know the ID of the refund.
  This endpoint allows an API client to void a refund using _only_ the
  idempotency key to recover from these situations.


  If you don't have the idempotency key or ID of the refund you want to void,
  you can use the [ListRefunds](ref:list-refunds) endpoint to try to search for
  the refund you're looking for.


  **This endpoint is not rate limited.**


  Scopes: `REFUNDS_WRITE`
api:
  file: network-api.json
  operationId: void-refund-by-idempotency-key
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---