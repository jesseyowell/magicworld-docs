---
title: Upsert brand
excerpt: |-
  Creates or updates a brand based on the brand's `reference_id`.

  If a brand with a matching `reference_id` is found, 
  it will be updated. If no matching brand is found,
  a new one will be created.

  The HTTP response code (`200 OK` or `201 Created`) indicates
  whether the resource was updated or created, respectively.

  **This endpoint is not rate limited.**

  Scopes: `BRANDS_WRITE`
api:
  file: network-api.json
  operationId: upsert-brand
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---