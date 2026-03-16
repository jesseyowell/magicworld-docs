---
title: Track Profile Activity
excerpt: >-
  This endpoint is used to track a profile's activity. The following data is
  encoded in a JSON object. NOTE: an account can have up to 200 unique metrics
  (event types). This endpoint can accept payloads up to approximately 1MB.


    **JSON OBJECT STRUCTURE:**

    __token: *string*__
    This is your public API key.
    
    __event: *string*__
    Name of the event you want to track. 
    
    __customer_properties: *JSON Object or null*__
    Properties of the profile that triggered this event. You must identify the person by their email using a $email key (or by their phone number using a `$phone_number` key if you have SMS-only contacts). Other than that, you can include any data you want and it can then be used to create segments of people. For example, if you wanted to create a list of people on trial plans, include a person's plan type in this JSON object so you can use that information later.
    
    __properties: *optional; JSON Object or null*__
    Properties of this event. Any properties included here can be used for creating segments later For example, if you track an event called "Ordered Product" you could include a property for item type (e.g. image, article, etc.), size, etc.

    __time: *optional; 10-digit UNIX timestamp or null*__
    When this event occurred. By default, Klaviyo assumes events happen when a request is made. If you'd like to track an event that happened in past, use this property.
    
    
    **SPECIAL FIELDS:**
    
    The Klaviyo CRM has the following special fields you can set for **customer_properties** with the **Track** endpoint, to unlock additional functionality:
    
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
    
    You can also set the following special fields in event **properties** with the **Track** endpoint:
    
    **$event_id:** _a unique identifier for an event_
    **$value:** _a numeric value to associate with this event (e.g. the dollar value of a purchase)_
    
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
api:
  file: klaviyo-api.json
  operationId: track-post
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---