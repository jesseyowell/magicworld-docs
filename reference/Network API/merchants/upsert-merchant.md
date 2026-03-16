---
title: Upsert merchant
excerpt: |-
  Creates or updates a merchant based on the merchant's `reference_id`.

  If a merchant with a matching `reference_id` is found, 
  it will be updated. If no matching merchant is found,
  a new one will be created.

  The HTTP response code (`200 OK` or `201 Created`) indicates
  whether the resource was updated or created, respectively.

  Merchants must have an `address` or `site_url` set.

  **This endpoint is not rate limited.**

  Scopes: `MERCHANTS_WRITE`
api:
  file: network-api.json
  operationId: upsert-merchant
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---