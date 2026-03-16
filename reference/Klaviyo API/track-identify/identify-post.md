---
title: Identify Profile
excerpt: >-
  This endpoint is used to track and update properties about an individual
  without tracking an associated event. The following data is stored in a JSON
  object.


    **JSON OBJECT STRUCTURE:**

    __token: *string*__
    This is your public API key.
    
    __properties: *JSON Object or null*__
    Properties of the profile to track/update. You must identify the person by their email using a $email key (or by their phone number using a `$phone_number` key if you have SMS-only contacts). Other than that, you can include any data you want and it can then be used to create segments of people. For example, if you wanted to create a list of people on trial plans, include a person's plan type in this JSON object so you can use that information later.
    
    
    **SPECIAL FIELDS:**

    The Klaviyo CRM has the following special fields you can set for customer **properties** with the **Identify** endpoint, to unlock additional functionality:
    
    **$email:** _string_
    **$first_name:** _string_
    **$last_name:** _string_
    **$phone_number:** _string; eg: "+13239169023"_
    **$city:** _string_
    **$region:** _string; state, or other region_
    **$country:** _string_
    **$zip:** _string_
    **$image:** _string; url to a photo of a person_
    **$consent:** _list of strings; eg: ['sms', 'email', 'web', 'directmail', 'mobile']_
    
    
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
api:
  file: klaviyo-api.json
  operationId: identify-post
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---