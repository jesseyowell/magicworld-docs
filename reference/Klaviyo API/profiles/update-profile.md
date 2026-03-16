---
title: Update Profile
excerpt: >-
  NOTE: If you are interested in creating or updating profiles in Klaviyo, you
  should be using the Identify API instead. The best use-case for this route is
  changing a profiles's email address or other primary identifier after a
  profile already exists in Klaviyo.


  Add or update one more more attributes for a Person, based on the Klaviyo
  Person ID. If a property already exists, it will be updated. If a property is
  not set for that record, it will be created.


  You can update any attribute, by sending one or more attributes along their
  new values, as query parameters. Recommended attributes for this endpoint:
  `$email`, `$phone_number`, `$id`
api:
  file: klaviyo-api.json
  operationId: update-profile
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---