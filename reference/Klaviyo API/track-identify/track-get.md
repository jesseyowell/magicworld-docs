---
title: Track Profile Activity (Legacy)
excerpt: >-
  This endpoint is also used to track a profile's activity. It takes as input
  the same payload as the above POST request, but as a base64-encoded string
  passed as a query parameter. NOTE: This is offered for backwards
  compatibility; we recommend all new implementations use the POST approach
  above.
    
    **EXAMPLE:**
    
    ```
    {
      "token": "PUBLIC_KEY",
      "event": "Ordered Product",
      "customer_properties": {
        "$email": "abraham.lincoln@klaviyo.com"
      },
      "properties": {
        "item_name": "Boots",
        "$value": 100
      }
    }

    ```
    Gets encoded into the following string, which is passed into the `data` parameter:

    `eyJ0b2tlbiI6ICJQVUJMSUNfS0VZIiwiZXZlbnQiOiAiT3JkZXJlZEl0ZW0iLCJjdXN0b21lcl9wcm9wZXJ0aWVzIjogeyIkZW1haWwiOiAiYWJyYWhhbS5saW5jb2xuQGtsYXZpeW8uY29tIn0sInByb3BlcnRpZXMiOiB7Iml0ZW1fbmFtZSI6ICJCb290cyIsIiR2YWx1ZSI6IDEwMH19`
api:
  file: klaviyo-api.json
  operationId: track-get
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---