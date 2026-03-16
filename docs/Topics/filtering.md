---
title: Filtering
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
List endpoints can optionally include filters as query parameters in the request url. 

**Request**
```
GET https://api.finexio.com/v1/counterparties/?internal_id=GA127
```

**Response**
```
HTTP 200 OK
{
    "count": 2
    "next": null,
    "previous": null,
    "results": [
       …
    ]
}
```
[block:api-header]
{
  "title": "Combining Filters"
}
[/block]
When multiple filters are applied to a request, the returned results are the intersection of the filters applied. However, when the same filter is applied multiple times, the filtering system treats this as an OR operation. For example, the following request may return up to two results:
```
GET https://api.finexio.com/v1/counterparties/?internal_id=GA127&internal_id=GA211
```
[block:api-header]
{
  "title": "Available Filters"
}
[/block]
Filters are available for the following endpoints:
[block:parameters]
{
  "data": {
    "h-0": "endpoint",
    "h-1": "filter paramaters",
    "0-0": "/counterparties/",
    "0-1": "type=[buyer|supplier]\ninternal_id={value}"
  },
  "cols": 2,
  "rows": 1
}
[/block]

[block:callout]
{
  "type": "success",
  "title": "More Filters",
  "body": "If you have a filtering use case that is not covered above, just let us know!"
}
[/block]