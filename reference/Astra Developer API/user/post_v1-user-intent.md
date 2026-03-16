---
title: Create a User Intent
excerpt: >-
  > 📘

  > 

  > You can place your application's `client_id` into the `username` field, and
  your `client_secret` into the `password` form field of the Authentication
  section of this documentation 👉.      


  A User Intent manages the lifecycle of the creation of a User, before that
  User has been fully created. This endpoint creates a User Intent, starting the
  process of verifying the end-user's identity in the background.\n


  For managing UserIntents, Astra recommends that once a UserIntent is created,
  you should store that UserIntent ID with the User record. The UserIntent ID
  can then be sent as a query string parameter to the Astra OAuth flow. Once
  your application receives the `authorization_code`, you can make a call to the
  `GET /v1/user` endpoint which will give you a `user_id`.


  > 🚧

  > 

  > Note that a new UserIntent should only be created if an end-user is starting
  from scratch or had originally provided incorrect information.


  > 🚧

  > 

  > Note that if a UserIntent doesn't have an address2 value, send Astra an
  empty string instead of a null or you'll recieve a 400 response upon POSTing
  the request.


  > ❗️

  > 

  > Note that you may only attempt to create 3 UserIntents per email address. If
  you reach this limit while creating UserIntents in your Sandbox Environment,
  you will receive an error.
api:
  file: astra-developer-api.json
  operationId: post_v1-user-intent
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---