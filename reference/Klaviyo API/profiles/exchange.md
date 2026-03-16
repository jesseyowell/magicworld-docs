---
title: Exchange ID for Profile ID
excerpt: >-
  Klaviyo's web tracking uses an encrypted identifier. However, there are many
  use cases that require developers to have access to a given profile's email or
  phone number. In such cases, developers can use this operation to exchange an
  encrypted identifier for a profile ID, which they can then use to retrieve the
  full profile data (by making a subsequent request to the `get-profiles`
  operation).


  The `exchange_id` takes the following form:


  `<IDENTIFIER>.<COMPANY_ID>`


  The `exchange_id` appears in the url as follows:


  `?_kx=<IDENTIFIER>.<COMPANY_ID>`
api:
  file: klaviyo-api.json
  operationId: exchange
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---