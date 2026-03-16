---
title: Get a User Intent
excerpt: >-
  > 📘

  > 

  > You can place your application's `client_id` into the `username` field, and
  your `client_secret` into the `password` form field of the Authentication
  section of this documentation 👉.


  A User Intent manages the lifecycle of the creation of a User, before that
  User has been fully created. This endpoint retrieves the User Intent details.


  > 📘

  > 

  >  Note that the `user_id` will be returned in the payload if the UserIntent
  has been successfully converted to a User. Also note that a UserIntent does
  not need to have an Approved Status to be converted to a User.
api:
  file: astra-developer-api.json
  operationId: get_v1-user-intent-id
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---