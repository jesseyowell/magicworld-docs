---
title: Authorize a User
excerpt: >-
  > 📘

  > 

  > You can place your application's `client_id` into the `username` field, and
  your `client_secret` into the `password` form field of the Authentication
  section of this documentation 👉.


  Use this endpoint to both initially Authorize a User, and also to Refresh
  Authorization for a user.


  In the **Form Data** below, **Option 1** is for the initial action to
  Authorize a User.  **Option 2** is for the action of using the `refresh_token`
  to generate a new `access_token`.
api:
  file: astra-developer-api.json
  operationId: post_v1-oauth-token
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---