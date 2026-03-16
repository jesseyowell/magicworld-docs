---
title: Search REST API
excerpt: search search search
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
# Search Service REST API

# Search API

Search API provides apis to query elastic search.

## Search Request

### Curl Request structure

```bash
$ curl 'http://localhost:8080/api/v1/search' -i -X POST \
    -H 'Content-Type: application/json' \
    -H 'IDS-SESSION-ID: dummySesionID' \
    -d '{
    "entityType": "customer",
    "pageSize": 0,
    "pageOffset": 0,
    "recordsToReturn": 0,
    "recordOffset": 0,
    "sort": [
        {
            "fieldName": "customer.firstName",
             "order": "DESCENDING"
        }
    ],
     "filters": {
        "filter": [
            {
                "comparator": "EQUALS",
                "fieldName": "customer.fullAddress.stateCd",
                "fieldValue":  560093
            }
        ]
    },
    "search": "*"
}'
```

### Request Header

| Name             | Description                 |
| :--------------- | :-------------------------- |
| `Content-Type`   | Format of the request body. |
| `IDS-SESSION-ID` | Current session ID          |

### Sample Request structure

```none
{
    "entityType": "customer",
    "pageSize": 0,
    "pageOffset": 0,
    "recordsToReturn": 0,
    "recordOffset": 0,
    "sort": [
        {
            "fieldName": "customer.firstName",
             "order": "DESCENDING"
        }
    ],
     "filters": {
        "filter": [
            {
                "comparator": "EQUALS",
                "fieldName": "customer.fullAddress.stateCd",
                "fieldValue":  560093
            }
        ]
    },
    "search": "*"
}
```

### Request fields

| Path              | Type     | Description                                                                                                                                                                 |
| :---------------- | :------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `recordsToReturn` | `Number` | Number of search results to return.                                                                                                                                         |
| `pageSize`        | `Number` | Number of search results to return in a page.                                                                                                                               |
| `pageOffset`      | `Number` | Number of pages to skip. For example, pageOffset=2 indicates to skip the first 2 pages of the search results and return the third page of the search results. Default is 0. |
| `recordOffset`    | `Number` | Number of records to skip. For example, recordOffset=200 indicates to skip the first 200 search results and return the results starting from 201. Default is 0.             |
| `entityType`      | `String` | Name of the business entity within which you want to search. Default is all, which indicates to search across all business entities.                                        |
| `search`          | `String` | Search string. To retrieve all the records, use asterisk (\*).                                                                                                              |
| `sort`            | `Array`  | Specifies a list of fields based on which you want to sort the search results.                                                                                              |
| `filters`         | `Object` | Specifies a list of fields that you want to use as filters.                                                                                                                 |

### Response Header

| Name           | Description                  |
| :------------- | :--------------------------- |
| `Content-Type` | Format of the response body. |

### Sample Response structure

```none
{
  "status" : "OK",
  "startTime" : "11:01:32:652",
  "endTime" : "11:01:32:652",
  "timeTaken" : "1622570492653",
  "searchRequest" : {
    "search" : "*",
    "source" : [ ],
    "entityType" : "customer",
    "recordsToReturn" : 10,
    "recordOffset" : 0,
    "pageSize" : 0,
    "pageOffset" : 0,
    "filters" : {
      "filter" : [ {
        "fieldName" : "ONE.fullAddress.stateCd",
        "fieldValue" : 560093,
        "comparator" : "EQUALS"
      } ]
    },
    "sort" : [ {
      "fieldName" : "customer.firstName",
      "order" : "DESCENDING"
    } ],
    "debug" : false,
    "highlight" : false,
    "searchRequestType" : "GENERIC_SEARCH",
    "filterDeleted" : true
  },
  "searchResult" : {
    "hits" : 1,
    "pageSize" : 0,
    "pageOffset" : 0,
    "recordsToReturn" : 10,
    "recordOffset" : 0,
    "maxRecords" : 10000,
    "records" : [ {
      "customer.lastName" : "Halpert",
      "customer.fullAddress" : {
        "address" : "Address of Jim",
        "city" : "Bangalore",
        "addressType" : "Office",
        "stateCd" : 560093
      },
      "_meta" : {
        "score" : "1.0",
        "lastUpdateDate" : 1549901779564,
        "businessId" : "28590641461245541522428783314",
        "businessEntity" : "customer",
        "id" : "5c619fd34077c70001adead1",
        "state" : "ACTIVE",
        "type" : "customer",
        "status" : "ACTIVE"
      },
      "customer.firstName" : [ "Jim" ]
    } ]
  }
}
```

### Response fields

| Path                   | Type     | Description                                                                                   |
| :--------------------- | :------- | :-------------------------------------------------------------------------------------------- |
| `searchRequest`        | `Object` | Contains the search term and other attributes related to search.                              |
| `searchResult`         | `Object` | Contains the search results.                                                                  |
| `searchResult.hits`    | `Number` | Number of search results.                                                                     |
| `searchResult.records` | `Array`  | Contains all the search results that are filtered and sorted based on the specified criteria. |

## Suggest Request

### Curl Request structure

```bash
$ curl 'http://localhost:8080/api/v1/suggest' -i -X POST \
    -H 'Content-Type: application/json' \
    -H 'IDS-SESSION-ID: dummySessionId' \
    -d '{"debug": false,"recordsToReturn": 10,"entityType": "customer","suggests": {"term": "tom"}}'
```

### Request Header

| Name             | Description                 |
| :--------------- | :-------------------------- |
| `Content-Type`   | Format of the request body. |
| `IDS-SESSION-ID` | Current session ID          |

### Sample Request structure

```none
{"debug": false,"recordsToReturn": 10,"entityType": "customer","suggests": {"term": "tom"}}
```

### Request fields

| Path              | Type     | Description                                                 |
| :---------------- | :------- | :---------------------------------------------------------- |
| `recordsToReturn` | `Number` | Number of search results to return.                         |
| `entityType`      | `String` | Name of the business entity within which you want to search |
| `suggests`        | `Object` | String for which you want suggestions.                      |

### Response Header

| Name           | Description                  |
| :------------- | :--------------------------- |
| `Content-Type` | Format of the response body. |

### Sample Response structure

```none
{
  "status" : "OK",
  "startTime" : "11:01:33:620",
  "endTime" : "11:01:33:621",
  "searchRequest" : {
    "entityType" : "customer",
    "recordsToReturn" : 10,
    "suggests" : {
      "term" : "tom"
    },
    "entityTypes" : [ "customer" ],
    "debug" : false
  },
  "searchResult" : {
    "suggests" : [ {
      "suggest" : "Thomas",
      "entityType" : "customer"
    } ]
  }
}
```

### Response fields

| Path                    | Type     | Description                                                      |
| :---------------------- | :------- | :--------------------------------------------------------------- |
| `searchRequest`         | `Object` | Contains the search term and other attributes related to search. |
| `searchResult`          | `Object` | Contains the Suggest result.                                     |
| `searchResult.suggests` | `Array`  | Contains a list of suggestions for the specified string.         |

## Get-Metadata Request

### Curl Request structure

```bash
$ curl 'http://localhost:8080/api/v1/metadata' -i -X GET \
    -H 'IDS-SESSION-ID: dummySessionId' \
    -H 'MODEL_VERSION: modelVersion'
```

### Request Header

| Name             | Description        |
| :--------------- | :----------------- |
| `IDS-SESSION-ID` | Current session ID |

### Sample Request structure

```http
GET /api/v1/metadata HTTP/1.1
IDS-SESSION-ID: dummySessionId
MODEL_VERSION: modelVersion
Host: localhost:8080
```

### Response Header

| Name           | Description                  |
| :------------- | :--------------------------- |
| `Content-Type` | Format of the response body. |

### Sample Response structure

```none
{
  "businessEntities" : {
    "country" : {
      "Fields" : {
        "country.countryName" : {
          "label" : "countryName",
          "type" : "String"
        }
      },
      "SecondaryFields" : [ ],
      "FilterFields" : [ "country.countryCode" ],
      "SortFields" : [ "country.countryCode" ],
      "PrimaryFields" : [ "country.countryCode" ],
      "SuggestFields" : [ "country.countryCode" ]
    }
  },
  "searchConfiguration" : {
    "searchHistoryEnabled" : false,
    "autoSuggestMinCharToStartFrom" : 3,
    "showLabels" : true,
    "autoSuggestEnabled" : false,
    "searchPageSize" : 10,
    "searchHistoryMaxEntries" : 5,
    "autoSuggestMaxSuggestions" : 5,
    "searchOnSource" : false
  }
}
```

### Response fields

| Path                  | Type     | Description                                           |
| :-------------------- | :------- | :---------------------------------------------------- |
| `businessEntities`    | `Object` | List of all the business entities and their fields.   |
| `searchConfiguration` | `Object` | Displays the configuration details related to search. |

## Get-Entities Request

### Curl Request structure

```bash
$ curl 'http://localhost:8080/api/v1/entities' -i -X GET -H 'IDS-SESSION-ID: dummySessionId'
```

### Request Header

| Name             | Description        |
| :--------------- | :----------------- |
| `IDS-SESSION-ID` | Current session ID |

### Sample Request structure

```http
GET /api/v1/entities HTTP/1.1
IDS-SESSION-ID: dummySessionId
Host: localhost:8080
```

### Response Header

| Name           | Description                  |
| :------------- | :--------------------------- |
| `Content-Type` | Format of the response body. |

### Sample Response structure

```none
["prospect","customer"]
```

## Public Search Request

### Curl Request structure

```bash
$ curl 'http://localhost:8080/public/api/v1/search' -i -X POST \
    -H 'Content-Type: application/json' \
    -H 'IDS-SESSION-ID: dummySesionID' \
    -d '{
    "entityType": "customer",
    "pageSize": 0,
    "pageOffset": 0,
    "recordsToReturn": 0,
    "recordOffset": 0,
    "sort": [
        {
            "fieldName": "customer.firstName",
             "order": "DESCENDING"
        }
    ],
     "filters": {
        "filter": [
            {
                "comparator": "EQUALS",
                "fieldName": "customer.fullAddress.stateCd",
                "fieldValue":  560093
            }
        ]
    },
    "search": "*"
}'
```

### Request Header

| Name             | Description                 |
| :--------------- | :-------------------------- |
| `Content-Type`   | Format of the request body. |
| `IDS-SESSION-ID` | Current session ID          |

### Sample Request structure

```none
{
    "entityType": "customer",
    "pageSize": 0,
    "pageOffset": 0,
    "recordsToReturn": 0,
    "recordOffset": 0,
    "sort": [
        {
            "fieldName": "customer.firstName",
             "order": "DESCENDING"
        }
    ],
     "filters": {
        "filter": [
            {
                "comparator": "EQUALS",
                "fieldName": "customer.fullAddress.stateCd",
                "fieldValue":  560093
            }
        ]
    },
    "search": "*"
}
```

### Request fields

| Path              | Type     | Description                                                                                                                                                                 |
| :---------------- | :------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `recordsToReturn` | `Number` | Number of search results to return.                                                                                                                                         |
| `pageSize`        | `Number` | Number of search results to return in a page.                                                                                                                               |
| `pageOffset`      | `Number` | Number of pages to skip. For example, pageOffset=2 indicates to skip the first 2 pages of the search results and return the third page of the search results. Default is 0. |
| `recordOffset`    | `Number` | Number of records to skip. For example, recordOffset=200 indicates to skip the first 200 search results and return the results starting from 201. Default is 0.             |
| `entityType`      | `String` | Name of the business entity within which you want to search. Default is all, which indicates to search across all business entities.                                        |
| `search`          | `String` | Search string. To retrieve all the records, use asterisk (\*).                                                                                                              |
| `sort`            | `Array`  | Specifies a list of fields based on which you want to sort the search results.                                                                                              |
| `filters`         | `Object` | Specifies a list of fields that you want to use as filters.                                                                                                                 |

### Response Header

| Name           | Description                  |
| :------------- | :--------------------------- |
| `Content-Type` | Format of the response body. |

### Sample Response structure

```none
{
  "searchResult" : {
    "hits" : 1,
    "pageSize" : 0,
    "pageOffset" : 0,
    "recordsToReturn" : 10,
    "recordOffset" : 0,
    "maxRecords" : 10000,
    "records" : [ {
      "customer.lastName" : "Halpert",
      "customer.fullAddress" : {
        "address" : "Address of Jim",
        "city" : "Bangalore",
        "addressType" : "Office",
        "stateCd" : 560093
      },
      "_meta" : {
        "score" : "1.0",
        "lastUpdateDate" : 1549901779564,
        "businessId" : "28590641461245541522428783314",
        "businessEntity" : "customer",
        "id" : "5c619fd34077c70001adead1",
        "state" : "ACTIVE",
        "type" : "customer",
        "status" : "ACTIVE"
      },
      "customer.firstName" : [ "Jim" ]
    } ]
  }
}
```

### Response fields

| Path                   | Type     | Description                                                                                   |
| :--------------------- | :------- | :-------------------------------------------------------------------------------------------- |
| `searchResult`         | `Object` | Contains the search results.                                                                  |
| `searchResult.hits`    | `Number` | Number of search results.                                                                     |
| `searchResult.records` | `Array`  | Contains all the search results that are filtered and sorted based on the specified criteria. |
