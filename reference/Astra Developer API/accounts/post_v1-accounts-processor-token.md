---
title: Create Account by Plaid Processor Token
excerpt: >-
  > 📘

  > 

  > You can place the bearer `access_token` for a specific user into the
  Authentication section of this documentation 👉.


  Astra and Plaid have partnered to enable you to use your existing Plaid
  integration to connect bank accounts and leverage Astra's transfer automation
  capabilities.


  To get started, follow the guide from [Plaid's API
  docs](https://plaid.com/docs/auth/partnerships/astra/). Completing the process
  will result in the creation of a `processor_token`.


  Sending the `processor_token` to this endpoint will create an Account for a
  User within the Astra platform. You can then easily use the resulting account
  `id` as the source or destination of a transfer Routine.
api:
  file: astra-developer-api.json
  operationId: post_v1-accounts-processor-token
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---