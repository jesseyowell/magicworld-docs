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

## Combining Filters

When multiple filters are applied to a request, the returned results are the intersection of the filters applied. However, when the same filter is applied multiple times, the filtering system treats this as an OR operation. For example, the following request may return up to two results:

```
GET https://api.finexio.com/v1/counterparties/?internal_id=GA127&internal_id=GA211
```

## Available Filters

Filters are available for the following endpoints:

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        endpoint
      </th>

      <th>
        filter paramaters
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        /counterparties/
      </td>

      <td>
        type=[buyer|supplier]\
        internal\_id=\{value}
      </td>
    </tr>
  </tbody>
</Table>

> 👍 More Filters
>
> If you have a filtering use case that is not covered above, just let us know!
