---
title: Cancel Transfer
excerpt: >-
  > 📘

  > 

  > You can place the bearer `access_token` for a specific user into the
  Authentication section of this documentation 👉.


  Cancel a transfer for a user. To cancel a transfer, you must provide the ID of
  the transfer in the Endpoint URL. When a transfer is successfully canceled,
  Astra will return a successful response (HTTP 200) and the status of the
  transfer in the Transfer table will update to `canceled``.


  > 🚧

  > 

  >  Transfers can only be canceled if the request is made before the 5p ET / 2p
  PT cutoff on the first banking day after the Transfer was initiated, as
  defined by ACH regulations. Transfers cannot be canceled after that cutoff.
api:
  file: astra-developer-api.json
  operationId: post_v1-transfers-id-cancel
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---