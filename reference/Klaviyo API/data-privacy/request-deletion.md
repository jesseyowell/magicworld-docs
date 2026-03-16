---
title: Request a Deletion
excerpt: >-
  Request a data privacy-compliant deletion for the person record corresponding
  to an email address, phone number, or person identifier. 


  **If multiple person records exist for the provided identifier, only one of
  them will be deleted.**


  The arguments should be sent as content type application/json.         


  Note that only **one** identifier (email, phone_number, or person_id) can be
  specified.


  In addition to your API key, you need to set exactly one of the following
  parameters: `email`, `phone_number`, `or person_id`, along with the associated
  `string` value. 


  Examples:


  Email:

    `{"email":"abraham.lincoln@klaviyo.com"}`
    
  Phone Number:
    
    `{"phone_number":"+13239169023"}`
    
  Person ID:
    
    `{"person_id":"PERSON_ID"}`
api:
  file: klaviyo-api.json
  operationId: request-deletion
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---