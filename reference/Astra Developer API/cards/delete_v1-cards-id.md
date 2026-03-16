---
title: Delete a Card
excerpt: >-
  > 📘

  > 

  > You can place the bearer `access_token` for a specific user into the
  Authentication section of this documentation 👉.


  This endpoint deletes a debit card by way of a card's unique ID. If the card
  is successfully deleted, you'll receive an HTTP 200 OK response.


  > 🚧

  > 

  >  Astra will only delete cards that were added by the requesting OAuth
  Client. End-users can delete cards through the Web App.


  > ❗️

  > 

  >  A card can only be deleted if there are no active routines or pending
  transfers associated with it.
api:
  file: astra-developer-api.json
  operationId: delete_v1-cards-id
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---