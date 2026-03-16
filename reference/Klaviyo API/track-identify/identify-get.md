---
title: Identify Profile (Legacy)
excerpt: >-
  This endpoint is also used to identify a profile and update its properties
  without an associated event. It takes as input the same payload as the above
  POST request, but as a base64-encoded string passed as a query parameter.
  NOTE: This is offered for backwards compatibility; we recommend all new
  implementations use the POST approach above.

    **EXAMPLE:**
    
    ```
    {
        "token": "PUBLIC_KEY",
        "properties": {
          "$email": "abraham.lincoln@klaviyo.com",
          "$first_name": "Abraham",
          "$last_name": "Lincoln",
          "$city": "Springfield",
          "$region": "Illinois"
        }
    }
    ```
    Gets encoded into the following string, which is passed into the `data` parameter:

    `eyJ0b2tlbiI6ICJQVUJMSUNfS0VZIiwicHJvcGVydGllcyI6IHsiJGVtYWlsIjogImFicmFoYW0ubGluY29sbkBrbGF2aXlvLmNvbSIsIiRmaXJzdF9uYW1lIjogIkFicmFoYW0iLCIkbGFzdF9uYW1lIjogIkxpbmNvbG4iLCIkY2l0eSI6ICJTcHJpbmdmaWVsZCIsIiRyZWdpb24iOiAiSWxsaW5vaXMifX0K`
api:
  file: klaviyo-api.json
  operationId: identify-get
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---