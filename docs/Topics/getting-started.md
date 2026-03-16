---
title: Pagination
excerpt: ''
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
Whenever you query an endpoint that returns a list of objects, regardless of the number of objects returned, you will receive a response that includes pagination metadata. Additionally, all paginated endpoints *optionally* accept a single page number in the request query parameters.

**Request**
```
GET https://api.finexio.com/v1/invoices/?page=4
```

**Response**
```
HTTP 200 OK
{
    "count": 100
    "next": "https://api.finexio.com/v1/invoices/?page=5",
    "previous": "https://api.finexio.com/v1/invoices/?page=3",
    "results": [
       …
    ]
}
```

[block:callout]
{
  "type": "warning",
  "title": "Default Page Size",
  "body": "Maximum page size is 100. If you would like to have control over the page size for your requests, please let us know."
}
[/block]