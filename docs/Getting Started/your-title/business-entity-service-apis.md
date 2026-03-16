---
title: Business Entity Service APIs
excerpt: Business Entity Service APIs
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
# Business Entity Service APIs

# Introduction

REST APIs can be used to perform operations over the following objects:

- Source (XREF) Business Entity records
- Master (Active) Business Entity records
- Source (XREF) Relationship records
- Master (Active) Relationship records
- Change lists
- Links/Lineage
- Lookup values

Additionally, Graph API allows for traversing Business Entity relationship graphs.

Refer to the Business Entity service design [wiki page](https://infawiki.informatica.com/pages/viewpage.action?spaceKey=DF&title=Business+Entity+Service+REST+API#BusinessEntityServiceRESTAPI-BusinessEntityService) for additional information.

## HTTP Methods

You can access all Business Entity service REST APIs using the standard POST, PUT, PATCH, DELETE and GET methods.

## Authentication

- All communication with the Business Entity service will be secured via HTTPS and certificate-based authentication.
- To authenticate a security context, the caller must pass a valid session ID (IDS-SESSION-ID). Calls originated from another service will be authenticated using the calling service SSL certificate.

## APIs

### Change List

#### Create New Change List

##### Purpose

Create a new change list in Active state.

##### Sample Request

```http
POST /api/v1/changelist HTTP/1.1
Content-Type: application/json;charset=UTF-8
Accept: application/json
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
Content-Length: 130

{
  "owners" : [ "userA1", "userB1" ],
  "ownersGroups" : [ "groupA1", "groupB1" ],
  "parameters" : {
    "key1" : "value1"
  }
}
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Request Fields

| Path           | Type     | Description             |
| :------------- | :------- | :---------------------- |
| `owners`       | `Array`  | Change list owners      |
| `ownersGroups` | `Array`  | Change list owner group |
| `parameters`   | `Object` | Parameters              |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path           | Type     | Description                |
| :------------- | :------- | :------------------------- |
| `owners`       | `Array`  | Change list owners         |
| `ownersGroups` | `Array`  | Change list owner group    |
| `parameters`   | `Object` | Parameters                 |
| `id`           | `String` | Change list identifier     |
| `creator`      | `String` | Change list creator        |
| `state`        | `String` | State for new change lists |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
Content-Type: application/json;charset=UTF-8
Content-Length: 308

{
  "owners" : [ "userA1", "userB1" ],
  "ownersGroups" : [ "groupA1", "groupB1" ],
  "parameters" : {
    "key1" : "value1"
  },
  "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
  "creator" : "testUserName",
  "changes" : [ ],
  "state" : "ACTIVE",
  "creationDate" : 1623956110440,
  "lastUpdateDate" : 1623956110440
}
```

#### Query Change List

##### Purpose

The Query Change List REST API queries and returns all Change List records. A user can filter a Change List record by the ACTIVE, ABANDONED or PROMOTED state and can view only records created by a respective user. A user with adminnistrative privileges can view all Change List records..

##### Sample Request

```http
GET /api/v1/changelist?_state=ACTIVE&_page=0&_size=4 HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Accept: application/json
Host: business-entity
```

##### Request parameters

| Parameter | Description                                                  |
| :-------- | :----------------------------------------------------------- |
| `_state`  | The state is optional. The three states are *(wild card), ACTIVE, ABANDONED and PROMOTED. If the state is not set, the API call returns all records. If the state is set, only records with the requested state is returned. |
| `_page`   | Number of the page to return. Default value is 0             |
| `_size`   | Size of the page. Default value is 10                        |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path                      | Type      | Description                |
| :------------------------ | :-------- | :------------------------- |
| `first`                   | `Boolean` | First                      |
| `last`                    | `Boolean` | Last                       |
| `page`                    | `Number`  | Page to query              |
| `size`                    | `Number`  | Page size                  |
| `numberOfElements`        | `Number`  | Number of elements         |
| `content`                 | `Array`   | Response content           |
| `content.[].owners`       | `Array`   | Change list owners         |
| `content.[].ownersGroups` | `Array`   | Change list owner group    |
| `content.[].parameters`   | `Object`  | Parameters                 |
| `content.[].id`           | `String`  | Change list identifier     |
| `content.[].creator`      | `String`  | Change list creator        |
| `content.[].state`        | `String`  | State for new change lists |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
Content-Type: application/json;charset=UTF-8
Content-Length: 1477

{
  "first" : true,
  "last" : false,
  "page" : 0,
  "size" : 4,
  "numberOfElements" : 4,
  "totalNumberOfElements" : 5,
  "content" : [ {
    "owners" : [ "userA1", "userB1" ],
    "ownersGroups" : [ "groupA1", "groupB1" ],
    "parameters" : {
      "key1" : "value1"
    },
    "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
    "creator" : "testUserName",
    "changes" : [ ],
    "state" : "ACTIVE",
    "creationDate" : 1623956110309,
    "lastUpdateDate" : 1623956110309
  }, {
    "owners" : [ "userA2", "userB2" ],
    "ownersGroups" : [ "groupA2", "groupB2" ],
    "parameters" : {
      "key2" : "value2"
    },
    "id" : "2aaaaaaaaaaaaaaaaaaaaaaa",
    "creator" : "testUserName",
    "changes" : [ ],
    "state" : "ACTIVE",
    "creationDate" : 1623956110313,
    "lastUpdateDate" : 1623956110313
  }, {
    "owners" : [ "userA3", "userB3" ],
    "ownersGroups" : [ "groupA3", "groupB3" ],
    "parameters" : {
      "key3" : "value3"
    },
    "id" : "3aaaaaaaaaaaaaaaaaaaaaaa",
    "creator" : "testUserName",
    "changes" : [ ],
    "state" : "ACTIVE",
    "creationDate" : 1623956110316,
    "lastUpdateDate" : 1623956110316
  }, {
    "owners" : [ "userA4", "userB4" ],
    "ownersGroups" : [ "groupA4", "groupB4" ],
    "parameters" : {
      "key4" : "value4"
    },
    "id" : "4aaaaaaaaaaaaaaaaaaaaaaa",
    "creator" : "testUserName",
    "changes" : [ ],
    "state" : "ACTIVE",
    "creationDate" : 1623956110321,
    "lastUpdateDate" : 1623956110321
  } ]
}
```

#### Get Change List by ID

##### Purpose

The Get Change List by ID REST API returns change list records by the Change List ID.

##### Path parameters

| Parameter      | Description    |
| :------------- | :------------- |
| `changeListId` | Change list ID |

##### Sample Request

```http
GET /api/v1/changelist/1aaaaaaaaaaaaaaaaaaaaaaa HTTP/1.1
Content-Type: application/json;charset=UTF-8
Accept: application/json
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path           | Type     | Description                |
| :------------- | :------- | :------------------------- |
| `owners`       | `Array`  | Change list owners         |
| `ownersGroups` | `Array`  | Change list owner group    |
| `parameters`   | `Object` | Parameters                 |
| `id`           | `String` | Change list identifier     |
| `creator`      | `String` | Change list creator        |
| `state`        | `String` | State for new change lists |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
Content-Type: application/json;charset=UTF-8
Content-Length: 308

{
  "owners" : [ "userA1", "userB1" ],
  "ownersGroups" : [ "groupA1", "groupB1" ],
  "parameters" : {
    "key1" : "value1"
  },
  "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
  "creator" : "testUserName",
  "changes" : [ ],
  "state" : "ACTIVE",
  "creationDate" : 1623956110204,
  "lastUpdateDate" : 1623956110204
}
```

#### Promote or abandon change list

##### Purpose

The Promote/Abandon Change List REST API updates pending records within the change list by applying an appropriate state transition.

Note: Sometimes "promote" operation is also called "approve", and "abandon" operation is also called "reject".

##### Promote Change List example

###### Path parameters

| Parameter      | Description    |
| :------------- | :------------- |
| `changeListId` | Change list ID |

###### Sample Request

```http
POST /api/v1/changelist/1aaaaaaaaaaaaaaaaaaaaaaa HTTP/1.1
Content-Type: application/json;charset=UTF-8
Accept: application/json
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity

_action=promote
```

###### Request parameters

| Parameter | Description        |
| :-------- | :----------------- |
| `_action` | Promote or Abandon |

###### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

###### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `X_INFA_LOG_CTX` | Correlation ID                  |

###### Response Fields

| Path           | Type     | Description                |
| :------------- | :------- | :------------------------- |
| `owners`       | `Array`  | Change list owners         |
| `ownersGroups` | `Array`  | Change list owner group    |
| `parameters`   | `Object` | Parameters                 |
| `id`           | `String` | Change list identifier     |
| `creator`      | `String` | Change list creator        |
| `state`        | `String` | State for new change lists |

###### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
Content-Type: application/json;charset=UTF-8
Content-Length: 345

{
  "owners" : [ "userA1", "userB1" ],
  "ownersGroups" : [ "groupA1", "groupB1" ],
  "parameters" : {
    "key1" : "value1"
  },
  "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
  "creator" : "testUserName",
  "changes" : [ ],
  "state" : "PROMOTED",
  "promotionDate" : 1623956110534,
  "creationDate" : 1623956110528,
  "lastUpdateDate" : 1623956110534
}
```

##### Abandon Change List example

```TODO POST /api/v1/changelist/{changelistid}?_action=abandon```

### Links REST API

#### Form Group

##### Purpose

Create a new Business Entity record ID for the new group. By default (or if `_regroup=false`) the API call returns the current group leaders for the provided records and links the them to the new group. If `_regroup=true`, the API call links provided records without looking for leaders. If provided records are part of another group, the records are deleted from the other group.

##### Path parameters

| Parameter        | Description     |
| :--------------- | :-------------- |
| `businessEntity` | Business Entity |

##### Sample Request

```http
POST /api/v1/entity-group/customer?_regroup=false HTTP/1.1
Content-Type: application/json;charset=UTF-8
Accept: application/json
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
Content-Length: 212

[ {
  "businessEntity" : "customer",
  "id" : {
    "sourceSystem" : "HR",
    "sourcePKey" : "100"
  }
}, {
  "businessEntity" : "customer",
  "id" : {
    "sourceSystem" : "HR",
    "sourcePKey" : "101"
  }
} ]
```

##### Request parameters

| Parameter  | Description                                                  |
| :--------- | :----------------------------------------------------------- |
| `_regroup` | The default value is FALSE.FALSE - for given IDs find leaders and build new group TRUE - extract the given IDs into separate group |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description          |
| :--------------- | :------------------- |
| `MODEL_VERSION`  | Model version        |
| `Location`       | Internal ID location |
| `X_INFA_LOG_CTX` | Correlation ID       |

##### Sample Response

```http
HTTP/1.1 201 Created
X_INFA_LOG_CTX: correlationID
Location: https://business-entity/api/v1/entity-group/customer/1aaaaaaaaaaaaaaaaaaaaaaa
MODEL_VERSION: 1623956873965
```

#### Find Group Records for a List of Business Entity Record IDs

##### Purpose

Retrieves a list of contributors or the associated master record. Find group records for a list of Business Entity record IDs. The group records are a list of objects with ID’s and group leader properties. The API call returns group leader records only if the parameter `_leader=true` is passed, else - the `_groupIds` are returned directly. `_groupIds` contains a list of identifiers in JSON format. Either source record identifier: Combination of business entity name, external system name, and PKey of record in the external system, or a master record identifier: Combination of business entity name and internal ID of the record.

##### Path parameters

| Parameter        | Description          |
| :--------------- | :------------------- |
| `businessEntity` | Business entity name |

##### Sample Request

```http
GET /api/v1/entity-group/dealership?_groupIds=%5B%7B%22businessEntity%22%3A%22dealership%22%2C%22id%22%3A%7B%22sourceSystem%22%3A%22HR%22%2C%22sourcePKey%22%3A%22xd1%22%7D%7D%5D&_leader=true HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request parameters

| Parameter   | Description                 |
| :---------- | :-------------------------- |
| `_groupIds` | Group IDs                   |
| `_leader`   | If return group leader only |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `MODEL_VERSION`  | Model version                   |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956875145
Content-Type: application/json;charset=UTF-8
Content-Length: 194

{
  "numberOfElements" : 1,
  "content" : [ {
    "id" : {
      "businessEntity" : "dealership",
      "id" : {
        "sourceSystem" : "HR",
        "sourcePKey" : "xd1"
      }
    }
  } ]
}
```

#### Get Group

##### Purpose

Retrieves the business entity group

##### Path parameters

| Parameter        | Description     |
| :--------------- | :-------------- |
| `businessEntity` | Business Entity |
| `internalId`     | Internal ID     |

##### Request structure

```http
GET /api/v1/entity-group/customer/1aaaaaaaaaaaaaaaaaaaaaaa?_states=ACTIVE HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request parameters

| Parameter | Description                   |
| :-------- | :---------------------------- |
| `_states` | Find records with given state |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `X_INFA_LOG_CTX` | Correlation ID                  |
| `MODEL_VERSION`  | Model version                   |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956874213
Content-Type: application/json;charset=UTF-8
Content-Length: 816

{
  "id" : {
    "businessEntity" : "customer",
    "id" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  },
  "reason" : {
    "matches" : [ {
      "businessEntity" : "customer",
      "id" : {
        "sourceSystem" : "HR",
        "sourcePKey" : "100"
      }
    }, {
      "businessEntity" : "customer",
      "id" : {
        "sourceSystem" : "HR",
        "sourcePKey" : "101"
      }
    } ],
    "rawMatch" : null
  },
  "_meta" : {
    "editXref" : false,
    "createdBy" : "testUserName",
    "creationDate" : 1623956873962,
    "updatedBy" : "testUserName",
    "lastUpdateDate" : 1623956873962,
    "modelVersion" : "1",
    "states" : {
      "base" : "ACTIVE",
      "consolidation" : "MATCH_DIRTY",
      "searchIndex" : "SEARCH_DIRTY"
    },
    "changeList" : null,
    "jobId" : null,
    "type" : "customer"
  }
}
```

#### Unlink Member

##### Purpose

The Unlink Member REST API deletes incorrect matches from the group.

##### Path parameters

| Parameter        | Description     |
| :--------------- | :-------------- |
| `businessEntity` | Business Entity |
| `internalId`     | Internal ID     |

##### Sample Request

```http
DELETE /api/v1/entity-group/customer/1aaaaaaaaaaaaaaaaaaaaaaa HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `MODEL_VERSION`  | Model version  |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 204 No Content
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956874818
```

#### Get Lineage of Business Entity Records

##### Purpose

Return a lineage tree for a Business Entity record. The lineage tree includes every record of the Business Entity lifecycle.

##### Path parameters

| Parameter        | Description     |
| :--------------- | :-------------- |
| `businessEntity` | Business Entity |
| `internalId`     | Internal ID     |

##### Sample Request

```http
GET /api/v1/entity-lineage/customer/1aaaaaaaaaaaaaaaaaaaaaaa?_page=0&_size=5 HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request parameters

| Parameter | Description |
| :-------- | :---------- |
| `_page`   | Page number |
| `_size`   | Page size   |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `MODEL_VERSION`  | Model version                   |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path                                           | Type      | Description                                  |
| :--------------------------------------------- | :-------- | :------------------------------------------- |
| `first`                                        | `Boolean` | First                                        |
| `last`                                         | `Boolean` | Last                                         |
| `page`                                         | `Number`  | Page to query                                |
| `size`                                         | `Number`  | Page size                                    |
| `numberOfElements`                             | `Number`  | Number of elements                           |
| `content`                                      | `Array`   | Response content                             |
| `content.[].id`                                | `Object`  | ID                                           |
| `content.[].id.businessEntity`                 | `String`  | Business entity name                         |
| `content.[].id.id`                             | `Varies`  | ID Object                                    |
| `content.[].id.id.sourceSystem`                | `String`  | Source system                                |
| `content.[].id.id.sourcePKey`                  | `String`  | Source primary key                           |
| `content.[].reason`                            | `Object`  | Reason                                       |
| `content.[].reason.matches`                    | `Array`   | Matches records                              |
| `content.[].reason.matches.[].businessEntity`  | `String`  | Business entity name                         |
| `content.[].reason.matches.[].id`              | `Varies`  | ID Object                                    |
| `content.[].reason.matches.[].id.sourceSystem` | `String`  | Source system                                |
| `content.[].reason.matches.[].id.sourcePKey`   | `String`  | Source primary key                           |
| `content.[].reason.rawMatch`                   | `String`  | Raw match                                    |
| `content.[].parent`                            | `Object`  | Parent object                                |
| `content.[].parent.sourceSystem`               | `String`  | Source system                                |
| `content.[].parent.sourcePKey`                 | `String`  | Source primary key                           |
| `content.[]._meta`                             | `Object`  | Metadata Object                              |
| `content.[]._meta.changeList`                  | `Null`    | Change list id, NULL if not in a change list |
| `content.[]._meta.createdBy`                   | `String`  | Created by user                              |
| `content.[]._meta.creationDate`                | `Number`  | Creation date                                |
| `content.[]._meta.updatedBy`                   | `String`  | Updated by user                              |
| `content.[]._meta.lastUpdateDate`              | `Number`  | Last updated date                            |
| `content.[]._meta.modelVersion`                | `String`  | Current model version                        |
| `content.[]._meta.states`                      | `Object`  | Current states                               |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956875631
Content-Type: application/json;charset=UTF-8
Content-Length: 2385

{
  "first" : true,
  "last" : true,
  "page" : 0,
  "size" : 5,
  "sort" : [ ],
  "numberOfElements" : 3,
  "content" : [ {
    "id" : {
      "businessEntity" : "customer",
      "id" : "1aaaaaaaaaaaaaaaaaaaaaaa"
    },
    "reason" : {
      "matches" : [ {
        "businessEntity" : "customer",
        "id" : {
          "sourceSystem" : "HR",
          "sourcePKey" : "100"
        }
      }, {
        "businessEntity" : "customer",
        "id" : {
          "sourceSystem" : "HR",
          "sourcePKey" : "101"
        }
      } ],
      "rawMatch" : null
    },
    "_meta" : {
      "editXref" : false,
      "createdBy" : "testUserName",
      "creationDate" : 1623956875480,
      "updatedBy" : "testUserName",
      "lastUpdateDate" : 1623956875480,
      "modelVersion" : "1",
      "states" : {
        "base" : "ACTIVE",
        "consolidation" : "MATCH_DIRTY",
        "searchIndex" : "SEARCH_DIRTY"
      },
      "changeList" : null,
      "jobId" : null,
      "type" : "customer"
    }
  }, {
    "id" : {
      "businessEntity" : "customer",
      "id" : {
        "sourceSystem" : "HR",
        "sourcePKey" : "100"
      }
    },
    "parent" : {
      "businessEntity" : "customer",
      "id" : "1aaaaaaaaaaaaaaaaaaaaaaa"
    },
    "_meta" : {
      "editXref" : false,
      "createdBy" : "testUserName",
      "creationDate" : 1623956875480,
      "updatedBy" : "testUserName",
      "lastUpdateDate" : 1623956875480,
      "modelVersion" : "1",
      "states" : {
        "base" : "ACTIVE",
        "consolidation" : "MATCH_DIRTY",
        "searchIndex" : "SEARCH_DIRTY"
      },
      "changeList" : null,
      "jobId" : null,
      "type" : "customer"
    }
  }, {
    "id" : {
      "businessEntity" : "customer",
      "id" : {
        "sourceSystem" : "HR",
        "sourcePKey" : "101"
      }
    },
    "parent" : {
      "businessEntity" : "customer",
      "id" : "1aaaaaaaaaaaaaaaaaaaaaaa"
    },
    "_meta" : {
      "editXref" : false,
      "createdBy" : "testUserName",
      "creationDate" : 1623956875480,
      "updatedBy" : "testUserName",
      "lastUpdateDate" : 1623956875480,
      "modelVersion" : "1",
      "states" : {
        "base" : "ACTIVE",
        "consolidation" : "MATCH_DIRTY",
        "searchIndex" : "SEARCH_DIRTY"
      },
      "changeList" : null,
      "jobId" : null,
      "type" : "customer"
    }
  } ]
}
```

#### Get Lineage of Relationship Records

##### Purpose

Retrieves the lineage of a relationship record identified by the internal ID. You can paginate the results.

TODO GET /api/v1/relationship-lineage/{relationship}/{relationshipRecordId}

#### Get Members of a Business Entity Record

##### Purpose

The Get Members of a Business Entity Record REST API returns members of a Business Entity record. The members defined as Business Entity are persisted records and at the lowest level of the tree. The records may be XREF’s or Business Entity records from another Business Entity.

##### Path parameters

| Parameter        | Description     |
| :--------------- | :-------------- |
| `businessEntity` | Business Entity |
| `internalId`     | Internal ID     |

##### Sample Request

```http
GET /api/v1/entity-member/customer/1aaaaaaaaaaaaaaaaaaaaaaa?_page=0&_size=5 HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request parameters

| Parameter | Description |
| :-------- | :---------- |
| `_page`   | Page number |
| `_size`   | Page size   |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `MODEL_VERSION`  | Model version                   |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path                         | Type      | Description          |
| :--------------------------- | :-------- | :------------------- |
| `first`                      | `Boolean` | First                |
| `last`                       | `Boolean` | Last                 |
| `page`                       | `Number`  | Page to query        |
| `size`                       | `Number`  | Page size            |
| `numberOfElements`           | `Number`  | Number of elements   |
| `content`                    | `Array`   | Response content     |
| `content.[].businessEntity`  | `String`  | Business entity name |
| `content.[].id`              | `Varies`  | ID Object            |
| `content.[].id.sourceSystem` | `String`  | Source system        |
| `content.[].id.sourcePKey`   | `String`  | Source primary key   |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956873566
Content-Type: application/json;charset=UTF-8
Content-Length: 359

{
  "first" : true,
  "last" : true,
  "page" : 0,
  "size" : 5,
  "sort" : [ ],
  "numberOfElements" : 2,
  "content" : [ {
    "businessEntity" : "customer",
    "id" : {
      "sourceSystem" : "HR",
      "sourcePKey" : "100"
    }
  }, {
    "businessEntity" : "customer",
    "id" : {
      "sourceSystem" : "HR",
      "sourcePKey" : "101"
    }
  } ]
}
```

#### Get Members of a Relationship Record

TODO GET /api/v1/relationship-member/{relationship}/{internalId}

#### Remove the association between a contributor and its master record (unlink member).

`TODO DELETE /api/v1/entity-group/{businessEntity}/{memberId} ==== Create a new master record by associating contributors (form group). TODO POST /api/v1/entity-group/{businessEntity} ==== Retrieve a list of source records identified by the internal ID of the record (get group). TODO GET /api/v1/entity-group/{businessEntity}/{businessEntityRecordId} ==== Retrieve a list of contributors or the associated master record (list groups). TODO GET /api/v1/entity-group/{businessEntity}`

#### Remove the association between a relationship contributor and its relationship record (unlink member).

`TODO DELETE /api/v1/relationship-group/{relationship}/{memberId} ==== Create a relationship record by associating contributors for which IDs are specified (form group). TODO POST /api/v1/relationship-group/{relationship} ==== Retrieve a list of relationship contributors identified by the internal ID of the relationship record (get group). TODO GET /api/v1/relationship-group/{relationship}/{relationshipRecordId} ==== Retrieve a list of relationship contributors and the associated relationship record identified by the relationship record ID (list groups). TODO GET /api/v1/relationship-group/{relationship}`

### Lookups

#### Read List of Lookup Values

##### Purpose

The Read List of Lookup Values REST API returns a list of available values to the client.

##### Path parameters

| Parameter            | Description          |
| :------------------- | :------------------- |
| `businessEntityGuid` | Business entity GUID |
| `lookupFieldPath`    | Lookup field path    |

##### Sample Request

```http
GET /api/v1/lookup/customer/address.stateCd?_masters=%7B%22address.countryCd%22%3A%22x1%22%7D&sourceSystem=demo.system.default.2 HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request parameters

| Parameter      | Description                                                  |
| :------------- | :----------------------------------------------------------- |
| `_masters`     | One or more master values                                    |
| `sourceSystem` | Optional parameter. The source system is the lookup value. If a system is SOURCE_PKEY, the resulting lookup values contain source primary keys instead of canonical values. If no source system is provided, canonical code values will be provided. |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `MODEL_VERSION`  | Model version                   |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path                    | Type      | Description        |
| :---------------------- | :-------- | :----------------- |
| `first`                 | `Boolean` | First              |
| `last`                  | `Boolean` | Last               |
| `page`                  | `Number`  | Page to query      |
| `size`                  | `Number`  | Page size          |
| `numberOfElements`      | `Number`  | Number of elements |
| `content`               | `Array`   | Response content   |
| `content.[].state_code` | `String`  | State code         |
| `content.[].state_name` | `String`  | State name         |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956630373
Content-Disposition: inline;filename=f.txt
Content-Type: application/json;charset=UTF-8
Content-Length: 248

{
  "first" : true,
  "last" : true,
  "page" : 0,
  "size" : 10,
  "sort" : [ ],
  "numberOfElements" : 2,
  "content" : [ {
    "state_code" : "x1",
    "state_name" : "Bavaria"
  }, {
    "state_code" : "x2",
    "state_name" : "Bavaria"
  } ]
}
```

#### Get Lookup Value

##### Purpose

The Get Lookup Value REST API verifies the existence of a code value and returns a consumable field for data to be stored within a lookup field.

##### Path parameters

| Parameter            | Description          |
| :------------------- | :------------------- |
| `businessEntityGuid` | Business entity GUID |
| `lookupFieldPath`    | Lookup field path    |
| `code`               | code value           |

##### Sample Request

```http
GET /api/v1/lookup/customer/address.countryCd/de HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request parameters

| Parameter      | Description                                                  |
| :------------- | :----------------------------------------------------------- |
| `sourceSystem` | Optional parameter. The source system which the lookup value is to be obtained for. If given system is SOURCE_PKEY, resulting lookup value contains source primary key instead of canonical value. If no source system is provided, canonical code values will be provided. |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `MODEL_VERSION`  | Model version                   |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path           | Type     | Description  |
| :------------- | :------- | :----------- |
| `country_code` | `String` | Country code |
| `country_name` | `String` | Country name |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956629508
Content-Type: application/json;charset=UTF-8
Content-Length: 57

{
  "country_code" : "de",
  "country_name" : "Germany"
}
```

### BES Master Records

#### Description

The BES Master Records REST API’s consists of GET, POST, PATCH and DELETE methods. The API consists of two sets of API’s and two services related to Master Records.

The following are the two services related to Master Records:

- Current Master Records: Records with the current Best Version of Truth.
- Inactive Master Records: Inactive or Historical Master records. The records may be merged with other records or are part of Lineage.

The following are the two sets of APIs exposed:

- Current Master Records.
- Current and Historical Master Records.

#### Preview BVT

TODO POST /api/v1/preview-entity/{businessEntity}/ Body of the POST record should contain a list of Business Entity IDs that will be merged to use to produce a new BVT. No data will be changed as a result of the preview call.

#### Read Master Record by ID

##### Purpose

The Read Master Record REST API returns records by Internal ID. If the ID enter in the API request points to Historical Master Record, the service will search and return the corresponding Active Record.

##### Path parameters

| Parameter        | Description     |
| :--------------- | :-------------- |
| `businessEntity` | Business Entity |
| `internalId`     | Internal ID     |

##### Sample Request

```http
GET /api/v1/entity/customer/1aaaaaaaaaaaaaaaaaaaaaaa HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `MODEL_VERSION`  | Model version                   |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path       | Type     | Description |
| :--------- | :------- | :---------- |
| `_meta.id` | `String` | ID          |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623957063795
Content-Type: application/json;charset=UTF-8
Content-Length: 752

{
  "firstName" : "firstName1",
  "lastName" : "lastName1",
  "prefix" : "Mr.",
  "deathStatusCode" : 1,
  "statusReasonCode" : 1,
  "language" : "English",
  "type" : 1,
  "suffix" : "",
  "statusChangeDate" : 1623957063597,
  "state" : "NEW",
  "id" : 1,
  "status" : 1,
  "version" : 1,
  "_meta" : {
    "businessEntity" : "customer",
    "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
    "createdBy" : "testUserName",
    "creationDate" : 1623957063618,
    "updatedBy" : "testUserName",
    "lastUpdateDate" : 1623957063618,
    "modelVersion" : "1",
    "states" : {
      "base" : "ACTIVE",
      "consolidation" : "MATCH_DIRTY",
      "searchIndex" : "SEARCH_DIRTY"
    },
    "businessId" : "29956720329104533486561830764",
    "status" : "ACTIVE"
  }
}
```

#### Read Master Record by SourcePKey

##### Purpose

The Read Master Record REST API returns records by sourceSystem sourcePKey pair.. If the ID enter in the API request points to Historical Master Record, the service will search and return the corresponding Active Record.

##### Path parameters

| Parameter        | Description               |
| :--------------- | :------------------------ |
| `businessEntity` | Business Entity           |
| `sourceSystem`   | source System             |
| `sourcePKey`     | Source system primary key |

##### Sample Request

```http
GET /api/v1/entity/customer/demo.system.default/x1 HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `MODEL_VERSION`  | Model version                   |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path                   | Type     | Description           |
| :--------------------- | :------- | :-------------------- |
| `firstName`            | `String` | First name            |
| `lastName`             | `String` | Last name             |
| `prefix`               | `String` | Prefix                |
| `deathStatusCode`      | `Number` | Death status code     |
| `statusReasonCode`     | `Number` | Status reason code    |
| `language`             | `String` | Language              |
| `type`                 | `Number` | Type                  |
| `suffix`               | `String` | Suffix                |
| `statusChangeDate`     | `Number` | Status change date    |
| `id`                   | `Number` | ID                    |
| `status`               | `Number` | Status                |
| `version`              | `Number` | Version               |
| `_meta`                | `Object` | Metadata Object       |
| `_meta.createdBy`      | `String` | Created by user       |
| `_meta.creationDate`   | `Number` | Creation date         |
| `_meta.updatedBy`      | `String` | Updated by user       |
| `_meta.lastUpdateDate` | `Number` | Last updated date     |
| `_meta.modelVersion`   | `String` | Current model version |
| `_meta.states`         | `Object` | Current states        |
| `_meta.businessId`     | `String` | Business ID           |
| `_meta.id`             | `String` | Internal ID           |
| `_meta.status`         | `String` | Status                |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623957063075
Content-Type: application/json;charset=UTF-8
Content-Length: 752

{
  "firstName" : "firstName1",
  "lastName" : "lastName1",
  "prefix" : "Mr.",
  "deathStatusCode" : 1,
  "statusReasonCode" : 1,
  "language" : "English",
  "type" : 1,
  "suffix" : "",
  "statusChangeDate" : 1623957062942,
  "state" : "NEW",
  "id" : 1,
  "status" : 1,
  "version" : 1,
  "_meta" : {
    "businessEntity" : "customer",
    "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
    "createdBy" : "testUserName",
    "creationDate" : 1623957062964,
    "updatedBy" : "testUserName",
    "lastUpdateDate" : 1623957062964,
    "modelVersion" : "1",
    "states" : {
      "base" : "ACTIVE",
      "consolidation" : "MATCH_DIRTY",
      "searchIndex" : "SEARCH_DIRTY"
    },
    "businessId" : "29956720310657789412852279145",
    "status" : "ACTIVE"
  }
}
```

#### Read Master Record by Business ID

##### Purpose

The Get Master Record by Business ID returns Active BE records for a given business ID. There can be many Inactive BE records and only one Active BE records with the same business ID. The API service returns Active Business Entity records.

##### Path parameters

| Parameter        | Description     |
| :--------------- | :-------------- |
| `businessEntity` | Business Entity |
| `businessId`     | Business ID     |

##### Sample Request

```http
GET /api/v1/entity/customer/business-id/29956720310657789412852279142 HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `MODEL_VERSION`  | Model version                   |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path       | Type     | Description |
| :--------- | :------- | :---------- |
| `_meta.id` | `String` | ID          |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623957062448
Content-Type: application/json;charset=UTF-8
Content-Length: 752

{
  "firstName" : "firstName1",
  "lastName" : "lastName1",
  "prefix" : "Mr.",
  "deathStatusCode" : 1,
  "statusReasonCode" : 1,
  "language" : "English",
  "type" : 1,
  "suffix" : "",
  "statusChangeDate" : 1623957062265,
  "state" : "NEW",
  "id" : 1,
  "status" : 1,
  "version" : 1,
  "_meta" : {
    "businessEntity" : "customer",
    "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
    "createdBy" : "testUserName",
    "creationDate" : 1623957062286,
    "updatedBy" : "testUserName",
    "lastUpdateDate" : 1623957062286,
    "modelVersion" : "1",
    "states" : {
      "base" : "ACTIVE",
      "consolidation" : "MATCH_DIRTY",
      "searchIndex" : "SEARCH_DIRTY"
    },
    "businessId" : "29956720310657789412852279142",
    "status" : "ACTIVE"
  }
}
```

#### Retrieve a master record identified by the internal ID.

##### Purpose

Retrieve Active or Inactive Master Record by internal ID. TODO GET /api/v1/group-entity/{businessEntity}/{id}

#### List/Filter Master Records

##### Purpose

List/Filter Active and Inactive Master Records API and return the matching BE records. The API call follows the general principles described in REST API Reference for services that return list of records.

Note: Virtual BE records are not persisted. you can only filter master records for persisted fields.

Two options are available for passing the filter - using GET or POST methods (see below).

##### Execute filter request Using GET

###### Path parameters

| Parameter        | Description     |
| :--------------- | :-------------- |
| `businessEntity` | Business Entity |

###### Sample Request

```http
GET /api/v1/group-entity/customer?filter=%7Btype%3A+1%7D HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

###### Request parameters

| Parameter | Description |
| :-------- | :---------- |
| `filter`  | Filter      |

###### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

###### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `MODEL_VERSION`  | Model version                   |
| `X_INFA_LOG_CTX` | Correlation ID                  |

###### Response Fields

| Path                              | Type      | Description           |
| :-------------------------------- | :-------- | :-------------------- |
| `first`                           | `Boolean` | First                 |
| `last`                            | `Boolean` | Last                  |
| `page`                            | `Number`  | Page to query         |
| `size`                            | `Number`  | Page size             |
| `numberOfElements`                | `Number`  | Number of elements    |
| `content`                         | `Array`   | Response content      |
| `content.[].firstName`            | `String`  | First name            |
| `content.[].lastName`             | `String`  | Last name             |
| `content.[].prefix`               | `String`  | Prefix                |
| `content.[].deathStatusCode`      | `Number`  | Death status code     |
| `content.[].statusReasonCode`     | `Number`  | Status reason code    |
| `content.[].language`             | `String`  | Language              |
| `content.[].type`                 | `Number`  | Type                  |
| `content.[].suffix`               | `String`  | Suffix                |
| `content.[].statusChangeDate`     | `Number`  | Status change date    |
| `content.[].id`                   | `Number`  | ID                    |
| `content.[].status`               | `Number`  | Status                |
| `content.[].version`              | `Number`  | Version               |
| `content.[]._meta`                | `Object`  | Metadata Object       |
| `content.[]._meta.createdBy`      | `String`  | Created by user       |
| `content.[]._meta.creationDate`   | `Number`  | Creation date         |
| `content.[]._meta.updatedBy`      | `String`  | Updated by user       |
| `content.[]._meta.lastUpdateDate` | `Number`  | Last updated date     |
| `content.[]._meta.modelVersion`   | `String`  | Current model version |
| `content.[]._meta.states`         | `Object`  | Current states        |
| `content.[]._meta.businessEntity` | `String`  | Business entity       |
| `content.[]._meta.businessId`     | `String`  | Business ID           |
| `content.[]._meta.status`         | `String`  | Status                |

###### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623957064533
Content-Type: application/json;charset=UTF-8
Content-Length: 940

{
  "first" : true,
  "last" : true,
  "page" : 0,
  "size" : 10,
  "sort" : [ ],
  "numberOfElements" : 1,
  "content" : [ {
    "firstName" : "firstName1",
    "lastName" : "lastName1",
    "prefix" : "Mr.",
    "deathStatusCode" : 1,
    "statusReasonCode" : 1,
    "language" : "English",
    "type" : 1,
    "suffix" : "",
    "statusChangeDate" : 1623957064383,
    "state" : "NEW",
    "id" : 1,
    "status" : 1,
    "version" : 1,
    "_meta" : {
      "businessEntity" : "customer",
      "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
      "createdBy" : "testUserName",
      "creationDate" : 1623957064413,
      "updatedBy" : "testUserName",
      "lastUpdateDate" : 1623957064413,
      "modelVersion" : "1",
      "states" : {
        "base" : "ACTIVE",
        "consolidation" : "MATCH_DIRTY",
        "searchIndex" : "SEARCH_DIRTY"
      },
      "businessId" : "29956720347551277560271382384",
      "status" : "ACTIVE"
    }
  } ]
}
```

##### Execute filter request Using POST

TODO POST /api/v1/group-entity/{businessEntity}/filter

#### Create BE Record

##### Purpose

Creates a record for the specified business entity. If users add a record, the operation also creates a source record that is associated with the record. If users update a record, the operation finds the associated source record or creates a source record and associates it with the record. Finally, the best version of the truth (BVT) is recalculated.

##### Path parameters

| Parameter        | Description     |
| :--------------- | :-------------- |
| `businessEntity` | Business Entity |

##### Sample Request

```http
POST /api/v1/entity/customer?sourceSystem=demo.system.default&sourcePKey=x1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Accept: application/json
Host: business-entity
Content-Length: 290

{
  "firstName" : "firstName1",
  "lastName" : "lastName1",
  "prefix" : "Mr.",
  "deathStatusCode" : 1,
  "statusReasonCode" : 1,
  "language" : "English",
  "type" : 1,
  "suffix" : "",
  "statusChangeDate" : 1623957062605,
  "state" : "NEW",
  "id" : 1,
  "status" : 1,
  "version" : 1
}
```

##### Request parameters

| Parameter      | Description               |
| :------------- | :------------------------ |
| `sourceSystem` | Source system             |
| `sourcePKey`   | Source system primary key |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Request Fields

| Path               | Type     | Description        |
| :----------------- | :------- | :----------------- |
| `firstName`        | `String` | First name         |
| `lastName`         | `String` | Last name          |
| `prefix`           | `String` | Prefix             |
| `deathStatusCode`  | `Number` | Death status code  |
| `statusReasonCode` | `Number` | Status reason code |
| `language`         | `String` | Language           |
| `type`             | `Number` | Type               |
| `suffix`           | `String` | Suffix             |
| `statusChangeDate` | `Number` | Status change date |
| `id`               | `Number` | ID                 |
| `status`           | `Number` | Status             |
| `version`          | `Number` | Version            |
| `state`            | `String` | State              |

##### Response Headers

| Name             | Description          |
| :--------------- | :------------------- |
| `MODEL_VERSION`  | Model version        |
| `Location`       | Internal ID location |
| `X_INFA_LOG_CTX` | Correlation ID       |

##### Sample Response

```http
HTTP/1.1 201 Created
X_INFA_LOG_CTX: correlationID
Location: https://business-entity/api/v1/entity/customer/1aaaaaaaaaaaaaaaaaaaaaaa
MODEL_VERSION: 1623957062608
```

#### Delete BE Record

##### Purpose

Deletes a record identified by the internal ID. TODO DELETE /api/v1/entity/{businessEntity}/{internalId}

#### Update BE Record by internal ID

##### Purpose

To update an existing Business Entity record by internal ID. TODO PUT /api/v1/entity/{businessEntity}/{internalId}?sourceSystem=<>[&sourcePKey=<>]

#### Patch BE Record by internal ID

##### Purpose

To patch an existing Business Entity record by internal ID. Unlike update, patch request does not replace complete Business Entity record, but only values specified as part of the request body.

##### Path parameters

| Parameter        | Description     |
| :--------------- | :-------------- |
| `businessEntity` | Business Entity |
| `internalId`     | Internal ID     |

##### Sample Request

```http
PATCH /api/v1/entity/customer/1aaaaaaaaaaaaaaaaaaaaaaa?sourceSystem=demo.system.default HTTP/1.1
Content-Type: application/bes-patch+json
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Accept: application/json
Host: business-entity
Content-Length: 83

[ {
  "op" : "replace",
  "path" : "firstName",
  "value" : "patchedFirstName1"
} ]
```

##### Request parameters

| Parameter      | Description   |
| :------------- | :------------ |
| `sourceSystem` | Source system |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Request Fields

| Path       | Type     | Description |
| :--------- | :------- | :---------- |
| `[]`       | `Array`  | Xref data   |
| `[].op`    | `String` | Operation   |
| `[].path`  | `String` | Path        |
| `[].value` | `String` | data        |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `MODEL_VERSION`  | Model version  |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 204 No Content
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623957064080
```

#### Update Master Record Identified by Business ID

##### Purpose

Update Master Record Identified by Business ID. The REST API updates existing BE records identified by Business ID.

##### Path parameters

Unresolved directive in business-entity-apis.adoc - include::/data/jenkins/workspace/uild_release_2021-07-M-Release_2/Src/bes-integration-tests/target/generated-snippets/update-be-record-by-business-id/path-parameters.adoc[]

##### Sample Request

Unresolved directive in business-entity-apis.adoc - include::/data/jenkins/workspace/uild_release_2021-07-M-Release_2/Src/bes-integration-tests/target/generated-snippets/update-be-record-by-business-id/http-request.adoc[]

##### Request parameters

Unresolved directive in business-entity-apis.adoc - include::/data/jenkins/workspace/uild_release_2021-07-M-Release_2/Src/bes-integration-tests/target/generated-snippets/update-be-record-by-business-id/request-parameters.adoc[]

##### Request Headers

Unresolved directive in business-entity-apis.adoc - include::/data/jenkins/workspace/uild_release_2021-07-M-Release_2/Src/bes-integration-tests/target/generated-snippets/update-be-record-by-business-id/request-headers.adoc[]

##### Request Fields

Unresolved directive in business-entity-apis.adoc - include::/data/jenkins/workspace/uild_release_2021-07-M-Release_2/Src/bes-integration-tests/target/generated-snippets/update-be-record-by-business-id/request-fields.adoc[]

##### Response Headers

Unresolved directive in business-entity-apis.adoc - include::/data/jenkins/workspace/uild_release_2021-07-M-Release_2/Src/bes-integration-tests/target/generated-snippets/update-be-record-by-business-id/response-headers.adoc[]

##### Sample Response

Unresolved directive in business-entity-apis.adoc - include::/data/jenkins/workspace/uild_release_2021-07-M-Release_2/Src/bes-integration-tests/target/generated-snippets/update-be-record-by-business-id/http-response.adoc[]

#### All Records of BE

##### Purpose

The All Records REST API returns current Active Master Records.

##### Path parameters

| Parameter        | Description     |
| :--------------- | :-------------- |
| `businessEntity` | Business Entity |

##### Sample Request

```http
GET /api/v1/entity/customer HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Accept: application/json
Host: business-entity
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `MODEL_VERSION`  | Model version                   |
| `Content-Type`   | The Content-Type of the payload |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623957063354
Content-Type: application/json;charset=UTF-8
Content-Length: 940

{
  "first" : true,
  "last" : true,
  "page" : 0,
  "size" : 10,
  "sort" : [ ],
  "numberOfElements" : 1,
  "content" : [ {
    "firstName" : "firstName1",
    "lastName" : "lastName1",
    "prefix" : "Mr.",
    "deathStatusCode" : 1,
    "statusReasonCode" : 1,
    "language" : "English",
    "type" : 1,
    "suffix" : "",
    "statusChangeDate" : 1623957063223,
    "state" : "NEW",
    "id" : 1,
    "status" : 1,
    "version" : 1,
    "_meta" : {
      "businessEntity" : "customer",
      "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
      "createdBy" : "testUserName",
      "creationDate" : 1623957063243,
      "updatedBy" : "testUserName",
      "lastUpdateDate" : 1623957063243,
      "modelVersion" : "1",
      "states" : {
        "base" : "ACTIVE",
        "consolidation" : "MATCH_DIRTY",
        "searchIndex" : "SEARCH_DIRTY"
      },
      "businessId" : "29956720329104533486561830763",
      "status" : "ACTIVE"
    }
  } ]
}
```

#### Filter a list of master records using POST.

You can filter, sort, and paginate the records TODO POST /api/v1/entity/{businessEntity}/filter

### XREF Relationship APIs

#### Upsert Relationship XREF

##### Purpose

Create or update a Relationship XREF record.

##### Path parameters

| Parameter      | Description               |
| :------------- | :------------------------ |
| `relationship` | Relationship              |
| `sourceSystem` | source System             |
| `sourcePKey`   | Source system primary key |

##### Sample Request

```http
PUT /api/v1/relationship-xref/DealershipToCustomer_ExistingCustomer/demo.system.default/pk1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
INFA-MDM-CHANGELIST-ID: 1aaaaaaaaaaaaaaaaaaaaaaa
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Accept: application/json
Host: business-entity
Content-Length: 331

{
  "id" : "~id~1",
  "profit" : 1000,
  "_from" : {
    "businessEntity" : "dealership",
    "id" : {
      "sourceSystem" : "demo.system.default",
      "sourcePKey" : "dx1"
    }
  },
  "_to" : {
    "businessEntity" : "customer",
    "id" : {
      "sourceSystem" : "demo.system.default",
      "sourcePKey" : "cx1"
    }
  }
}
```

##### Request Headers

| Name                     | Description            |
| :----------------------- | :--------------------- |
| `IDS-SESSION-ID`         | User Session ID        |
| `X-INFA-ORG-ID`          | Org ID                 |
| `X_INFA_LOG_CTX`         | Correlation ID         |
| `MODEL_VERSION`          | Metadata Model Version |
| `INFA-MDM-CHANGELIST-ID` | Change list ID         |

##### Request Fields

| Path                    | Type     | Description               |
| :---------------------- | :------- | :------------------------ |
| `id`                    | `String` | id                        |
| `profit`                | `Number` | Profit                    |
| `_from`                 | `Object` | From business entity      |
| `_from.businessEntity`  | `String` | Business entity name      |
| `_from.id`              | `Object` | Business entity id        |
| `_from.id.sourceSystem` | `String` | Source system             |
| `_from.id.sourcePKey`   | `String` | Source system primary key |
| `_to`                   | `Object` | To business entity        |
| `_to.businessEntity`    | `String` | Business entity name      |
| `_to.id`                | `Object` | Business entity id        |
| `_to.id.sourceSystem`   | `String` | Source system             |
| `_to.id.sourcePKey`     | `String` | Source system primary key |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `MODEL_VERSION`  | Model version  |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 204 No Content
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956021438
INFA-MDM-CHANGELIST-ID: 1aaaaaaaaaaaaaaaaaaaaaaa
```

#### Read Relationship XREF

##### Purpose

Read a Relationship XREF record identified by the primary key in a particular source system

##### Path parameters

| Parameter      | Description               |
| :------------- | :------------------------ |
| `relationship` | Relationship              |
| `sourceSystem` | source System             |
| `sourcePKey`   | Source system primary key |

##### Sample Request

```http
GET /api/v1/relationship-xref/DealershipToCustomer_ExistingCustomer/demo.system.default/pk1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
INFA-MDM-CHANGELIST-ID: 1aaaaaaaaaaaaaaaaaaaaaaa
Accept: application/json
Host: business-entity
```

##### Request Headers

| Name                     | Description            |
| :----------------------- | :--------------------- |
| `IDS-SESSION-ID`         | User Session ID        |
| `X-INFA-ORG-ID`          | Org ID                 |
| `X_INFA_LOG_CTX`         | Correlation ID         |
| `MODEL_VERSION`          | Metadata Model Version |
| `INFA-MDM-CHANGELIST-ID` | Change list ID         |

##### Response Headers

| Name                     | Description                     |
| :----------------------- | :------------------------------ |
| `MODEL_VERSION`          | Model version                   |
| `Content-Type`           | The Content-Type of the payload |
| `INFA-MDM-CHANGELIST-ID` | Change list ID                  |
| `X_INFA_LOG_CTX`         | Correlation ID                  |

##### Response Fields

| Path                    | Type     | Description               |
| :---------------------- | :------- | :------------------------ |
| `id`                    | `String` | id                        |
| `profit`                | `Number` | Profit                    |
| `_from`                 | `Object` | From business entity      |
| `_from.businessEntity`  | `String` | Business entity name      |
| `_from.id`              | `Object` | Business entity id        |
| `_from.id.sourceSystem` | `String` | Source system             |
| `_from.id.sourcePKey`   | `String` | Source system primary key |
| `_to`                   | `Object` | To business entity        |
| `_to.businessEntity`    | `String` | Business entity name      |
| `_to.id`                | `Object` | Business entity id        |
| `_to.id.sourceSystem`   | `String` | Source system             |
| `_to.id.sourcePKey`     | `String` | Source system primary key |
| `_meta`                 | `Object` | Metadata Object           |
| `_meta.relationship`    | `String` | Relationship              |
| `_meta.changeList`      | `String` | Change list               |
| `_meta.id`              | `Object` | ID object                 |
| `_meta.id.sourceSystem` | `String` | Source system             |
| `_meta.id.sourcePKey`   | `String` | Source primary key        |
| `_meta.createdBy`       | `String` | Created by user           |
| `_meta.creationDate`    | `Number` | Creation date             |
| `_meta.updatedBy`       | `String` | Updated by user           |
| `_meta.lastUpdateDate`  | `Number` | Last updated date         |
| `_meta.modelVersion`    | `String` | Current model version     |
| `_meta.states`          | `Object` | Current states            |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956021519
Content-Type: application/json;charset=UTF-8
INFA-MDM-CHANGELIST-ID: 1aaaaaaaaaaaaaaaaaaaaaaa
Content-Length: 877

{
  "_from" : {
    "businessEntity" : "dealership",
    "id" : {
      "sourceSystem" : "demo.system.default",
      "sourcePKey" : "dx1"
    }
  },
  "_to" : {
    "businessEntity" : "customer",
    "id" : {
      "sourceSystem" : "demo.system.default",
      "sourcePKey" : "cx1"
    }
  },
  "id" : "~id~1",
  "profit" : 1000,
  "_meta" : {
    "relationship" : "DealershipToCustomer_ExistingCustomer",
    "id" : {
      "sourceSystem" : "demo.system.default",
      "sourcePKey" : "pk1"
    },
    "createdBy" : "testUserName",
    "creationDate" : 1623956021455,
    "updatedBy" : "testUserName",
    "lastUpdateDate" : 1623956021455,
    "modelVersion" : "1",
    "states" : {
      "base" : "PENDING_CREATE",
      "consolidation" : "MATCH_DIRTY",
      "searchIndex" : "SEARCH_DIRTY"
    },
    "changeList" : "1aaaaaaaaaaaaaaaaaaaaaaa",
    "xrefType" : "DATA"
  }
}
```

#### Patch Relationship XREF

##### Purpose

Partially updates the relationship source record identified by the external system name and the PKey of the relationship record.

TODO PATCH /api/v1/relationship-xref/{relationship}/{sourceSystem}/{sourcePKey}

#### Delete Relationship XREF

##### Purpose

Delete a Relationship XREF record identified by the primary key in a particular source system

##### Path parameters

| Parameter      | Description               |
| :------------- | :------------------------ |
| `relationship` | Relationship              |
| `sourceSystem` | source System             |
| `sourcePKey`   | Source system primary key |

##### Sample Request

```http
DELETE /api/v1/relationship-xref/DealershipToCustomer_ExistingCustomer/demo.system.default/pk1 HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
INFA-MDM-CHANGELIST-ID: 1aaaaaaaaaaaaaaaaaaaaaaa
Accept: application/json
Host: business-entity
```

##### Request Headers

| Name                     | Description            |
| :----------------------- | :--------------------- |
| `IDS-SESSION-ID`         | User Session ID        |
| `X-INFA-ORG-ID`          | Org ID                 |
| `X_INFA_LOG_CTX`         | Correlation ID         |
| `MODEL_VERSION`          | Metadata Model Version |
| `INFA-MDM-CHANGELIST-ID` | Change list ID         |

##### Response Headers

| Name                     | Description    |
| :----------------------- | :------------- |
| `INFA-MDM-CHANGELIST-ID` | Change list ID |
| `MODEL_VERSION`          | Model version  |
| `X_INFA_LOG_CTX`         | Correlation ID |

##### Sample Response

```http
HTTP/1.1 204 No Content
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956021574
INFA-MDM-CHANGELIST-ID: 1aaaaaaaaaaaaaaaaaaaaaaa
```

### Active Relationship APIs

#### Read Active relationship by Internal ID

##### Purpose

The Read Active REST API returns the current Active records. You must provide the record ID in the request URL.

##### Path parameters

| Parameter      | Description  |
| :------------- | :----------- |
| `relationship` | Relationship |
| `internalId`   | Internal ID  |

##### Sample Request

```http
GET /api/v1/relationship/DealershipToCustomer_ExistingCustomer/6aaaaaaaaaaaaaaaaaaaaaaa HTTP/1.1
Content-Type: application/json;charset=UTF-8
Accept: application/json
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `MODEL_VERSION`  | Model version                   |
| `Content-Type`   | The Content-Type of the payload |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path                   | Type     | Description           |
| :--------------------- | :------- | :-------------------- |
| `id`                   | `String` | id                    |
| `profit`               | `Number` | Profit                |
| `_from`                | `Object` | From business entity  |
| `_from.businessEntity` | `String` | Business entity name  |
| `_from.id`             | `String` | Business entity id    |
| `_to`                  | `Object` | To business entity    |
| `_to.businessEntity`   | `String` | Business entity name  |
| `_to.id`               | `String` | Business entity id    |
| `_meta`                | `Object` | Metadata Object       |
| `_meta.id`             | `String` | ID                    |
| `_meta.status`         | `String` | Status                |
| `_meta.createdBy`      | `String` | Created by user       |
| `_meta.creationDate`   | `Number` | Creation date         |
| `_meta.updatedBy`      | `String` | Updated by user       |
| `_meta.lastUpdateDate` | `Number` | Last updated date     |
| `_meta.modelVersion`   | `String` | Current model version |
| `_meta.states`         | `Object` | Current states        |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956021098
Content-Type: application/json;charset=UTF-8
Content-Length: 660

{
  "_from" : {
    "businessEntity" : "dealership",
    "id" : "4aaaaaaaaaaaaaaaaaaaaaaa"
  },
  "_to" : {
    "businessEntity" : "customer",
    "id" : "2aaaaaaaaaaaaaaaaaaaaaaa"
  },
  "id" : "~id~1",
  "profit" : 1000,
  "_meta" : {
    "relationship" : "DealershipToCustomer_ExistingCustomer",
    "id" : "6aaaaaaaaaaaaaaaaaaaaaaa",
    "createdBy" : "testUserName",
    "creationDate" : 1623956020983,
    "updatedBy" : "testUserName",
    "lastUpdateDate" : 1623956020983,
    "modelVersion" : "1",
    "states" : {
      "base" : "ACTIVE",
      "consolidation" : "MATCH_DIRTY",
      "searchIndex" : "SEARCH_DIRTY"
    },
    "status" : "ACTIVE"
  }
}
```

#### Read Active relationship by Source system and Source Pkey

##### Purpose

Retrieves a relationship record identified by the external system name and the PKey of the record in the external system. TODO GET /api/v1/relationship/{relationshipGuid}/{sourceSystem}/{sourcePKey}

#### Filter active relationships using GET

##### Purpose

Retrieves a list of relationships. You can filter, sort, and paginate the relationships. TODO GET /api/v1/relationship/{relationshipGuid}

#### Filter active relationships using POST

##### Purpose

Retrieves a list of relationships. You can filter, sort, and paginate the relationships. TODO POST /api/v1/relationship/{relationshipGuid}/filter

#### Create New Active Relationship

##### Purpose

The Create New Active Relationship REST API creates a new XREF with user data and creates an ACTIVE relationship record with a single XREF as a member.

Note: Business Entity service API calls consolidates relationships of the same type with the same vertexes. The Create Rel API does not create several instances of the same relationship. The API verifies if there is an Active relationship between `_from` and `_to` vertexes provided in request. If an Active Relationship record already exists, the Create Rel API will create or update the Relationship XREF and link it to an existing Relationship record.

##### Path parameters

| Parameter      | Description  |
| :------------- | :----------- |
| `relationship` | Relationship |

##### Sample Request

```http
POST /api/v1/relationship/DealershipToCustomer_ExistingCustomer?sourceSystem=demo.system.default HTTP/1.1
Content-Type: application/json;charset=UTF-8
Accept: application/json
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
Content-Length: 223

{
  "id" : "~id~1",
  "profit" : 1000,
  "_from" : {
    "businessEntity" : "dealership",
    "id" : "4aaaaaaaaaaaaaaaaaaaaaaa"
  },
  "_to" : {
    "businessEntity" : "customer",
    "id" : "2aaaaaaaaaaaaaaaaaaaaaaa"
  }
}
```

##### Request parameters

| Parameter      | Description   |
| :------------- | :------------ |
| `sourceSystem` | Source system |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Request Fields

| Path                   | Type     | Description          |
| :--------------------- | :------- | :------------------- |
| `id`                   | `String` | id                   |
| `profit`               | `Number` | Profit               |
| `_from`                | `Object` | From business entity |
| `_from.businessEntity` | `String` | Business entity name |
| `_from.id`             | `String` | Business entity id   |
| `_to`                  | `Object` | To business entity   |
| `_to.businessEntity`   | `String` | Business entity name |
| `_to.id`               | `String` | Business entity id   |

##### Response Headers

| Name             | Description          |
| :--------------- | :------------------- |
| `MODEL_VERSION`  | Model version        |
| `Location`       | Internal ID location |
| `X_INFA_LOG_CTX` | Correlation ID       |

##### Sample Response

```http
HTTP/1.1 201 Created
X_INFA_LOG_CTX: correlationID
Location: https://business-entity/api/v1/relationship/DealershipToCustomer_ExistingCustomer/6aaaaaaaaaaaaaaaaaaaaaaa
MODEL_VERSION: 1623956020986
```

#### Update Active Relationship by internal ID

##### Purpose

Updates a relationship record identified by the internal ID. The operation creates a source record and then, updates the relationship record and associates it with the source record. TODO PUT /api/v1/relationship/{relationshipGuid}/{internalId}

#### Delete Active Relationship by internal ID

##### Purpose

Deletes a relationship record identified by the internal ID. TODO DELETE /api/v1/relationship/{relationshipGuid}/{internalId}

#### Patch Active Relationship by internal ID

##### Purpose

Partially updates a relationship record identified by the internal ID. TODO PATCH /api/v1/relationship/{relationshipGuid}/{internalId}

### Master Group Relationship API

#### Description

Master Group Relationship API allows for reading and filtering both active and inactive master relationship records.

#### Retrieve a relationship record identified by the internal ID

TODO GET /api/v1/group-relationship/{relationship}/{id}

#### Retrieve a list of relationships using a GET request

You can filter, sort, and paginate the relationships. TODO GET /api/v1/group-relationship/{relationship}

#### Filter a list of relationships using a POST request.

You can filter, sort, and paginate the relationships. TODO POST /api/v1/group-relationship/{relationship}/filter

### Business Entity Graph APIs

#### Description

Graph API only works with Active records.

If start record is not found, a 404 error with the following message is returned:

BE record not found. To optimize the data returned by the query, the following rules are applied: If the query returns collection of vertexes, only the ID of the BE record is returned. If query returns collection of edges, the complete Relationship record is returned.

#### Execute Graph query via GET using Business Entity internal ID as a starting point

Retrieves the data requested through a query, where the associated business entity is identified by the internal ID. You can retrieve information, such as a list of master records or relationship records or specific properties of the records. Also, you can retrieve aggregates, such as sums and counts.

The graph query is specified as part of request URL.

TODO GET /api/v1/graph/{relationshipSet}/{businessEntity}/{internalId}

#### Execute Graph query via POST using Business Entity internal ID as a starting point

Retrieves the data requested through a query, where the associated business entity is identified by the internal ID. You can retrieve information, such as a list of master records or relationship records or specific properties of the records. Also, you can retrieve aggregates, such as sums and counts.

The graph query is specified in the request body in JSON format.

TODO POST /api/v1/graph/{relationshipSet}/{businessEntity}/{internalId}

#### Execute Graph query via GET using Business Entity source primary key as a staring point

Retrieves the data requested through a query, where the business entity is identified by the PKey of the record in the external system.

The graph query is specified as part of request URL.

TODO GET /api/v1/graph/{relationshipSet}/{businessEntity}/{sourceSystem}/{sourcePKey}

#### Execute Graph query via POST using Business Entity source primary key as a staring point

Retrieves the data requested through a query, where the business entity is identified by the PKey of the record in the external system.

The graph query is specified in the request body in JSON format.

TODO POST /api/v1/graph/{relationshipSet}/{businessEntity}/{sourceSystem}/{sourcePKey}

### XREF Graph APIs

#### Description

XREF Graph API only works with Active XREF records.

If start record is not found, a 404 error with the following message is returned:

BE record not found. To optimize the data returned by the query, the following rules are applied: If the query returns collection of vertexes, only the ID of the BE record is returned. If query returns collection of edges, the complete Relationship record is returned.

#### Execute XREF Graph query via GET

##### Path parameters

| Parameter         | Description               |
| :---------------- | :------------------------ |
| `relationshipSet` | Relationship Set          |
| `businessEntity`  | Business Entity           |
| `sourceSystem`    | source System             |
| `sourcePKey`      | Source system primary key |

##### Sample Request

```http
GET /api/v1/graph-xref/january/prospect/demo.system.default/2?q=v.out%28%29.map%28%7Bv-%3Ev.get%28%29.id%28%29.businessEntityId%28%29%7D%29 HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request parameters

| Parameter | Description |
| :-------- | :---------- |
| `q`       | Graph query |

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `Content-Type`   | The Content-Type of the payload |
| `MODEL_VERSION`  | Model version                   |
| `X_INFA_LOG_CTX` | Correlation ID                  |

##### Response Fields

| Path               | Type      | Description        |
| :----------------- | :-------- | :----------------- |
| `first`            | `Boolean` | First              |
| `last`             | `Boolean` | Last               |
| `page`             | `Number`  | Page to query      |
| `size`             | `Number`  | Page size          |
| `numberOfElements` | `Number`  | Number of elements |
| `content`          | `Array`   | Response content   |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956201711
Content-Type: application/json;charset=UTF-8
Content-Length: 174

{
  "first" : true,
  "last" : true,
  "page" : 0,
  "size" : 10,
  "sort" : [ ],
  "numberOfElements" : 3,
  "content" : [ "dealership", "household", "marketingCampaign" ]
}
```

#### Execute XREF Graph query via POST

Retrieves the data requested through a query, where the business entity is identified by the PKey of the record in the external system. TODO POST /api/v1/graph-xref/{relationshipSet}/{businessEntity}/{sourceSystem}/{sourcePKey}

### Entity XREF

#### Upsert XREF

##### Purpose

The Upsert XREF API updates an existing record or creates a new record.

The logic behind Upsert XREF API is as follows:

- Updates an existing record or if a record with given sourceSystem/sourcePKey is not found, a new record is created.
- If a record is created, the service assigns a new business ID value. If record is updated, the business ID value does not change.
- If a existing record is soft-deleted, the service returns an error.

TODO PUT /api/v1/entity-xref/{businessEntity}/{sourceSystem}/{sourcePKey}

#### Patch XREF

##### Purpose

Partially updates a source record identified by the PKey of the record in the external system.

##### Sample Request

```http
PATCH /api/v1/entity-xref/customer/demo.system.default/c.1 HTTP/1.1
Content-Type: application/bes-patch+json
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Accept: application/json
Host: business-entity
Content-Length: 83

[ {
  "op" : "replace",
  "path" : "firstName",
  "value" : "patchedFirstName1"
} ]
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Request Fields

| Path       | Type     | Description |
| :--------- | :------- | :---------- |
| `[]`       | `Array`  | Xref data   |
| `[].op`    | `String` | Operation   |
| `[].path`  | `String` | Path        |
| `[].value` | `String` | data        |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `MODEL_VERSION`  | Model version  |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 204 No Content
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623955915373
```

#### Read XREF

##### Purpose

The Read XREF API retrieves the details of a source record identified by the PKey of the record in the source system.

##### Sample Request

```http
GET /api/v1/entity-xref/customer/demo.system.default/c.1 HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description                     |
| :--------------- | :------------------------------ |
| `MODEL_VERSION`  | Model version                   |
| `X_INFA_LOG_CTX` | Correlation ID                  |
| `Content-Type`   | The Content-Type of the payload |

##### Response Fields

| Path                    | Type     | Description           |
| :---------------------- | :------- | :-------------------- |
| `firstName`             | `String` | First name            |
| `lastName`              | `String` | Last name             |
| `prefix`                | `String` | Prefix                |
| `deathStatusCode`       | `Number` | Death status code     |
| `statusReasonCode`      | `Number` | Status reason code    |
| `language`              | `String` | Language              |
| `type`                  | `Number` | Type                  |
| `suffix`                | `String` | Suffix                |
| `statusChangeDate`      | `Number` | Status change date    |
| `id`                    | `Number` | ID                    |
| `status`                | `Number` | Status                |
| `version`               | `Number` | Version               |
| `partyState`            | `String` | Party state           |
| `birthDay`              | `Number` | Birthday              |
| `_meta`                 | `Object` | Metadata Object       |
| `_meta.businessEntity`  | `String` | Business entity name  |
| `_meta.id`              | `Varies` | ID Object             |
| `_meta.id.sourceSystem` | `String` | Source system         |
| `_meta.id.sourcePKey`   | `String` | Source primary key    |
| `_meta.businessId`      | `String` | Business ID           |
| `_meta.createdBy`       | `String` | Created by user       |
| `_meta.creationDate`    | `Number` | Creation date         |
| `_meta.updatedBy`       | `String` | Updated by user       |
| `_meta.lastUpdateDate`  | `Number` | Last updated date     |
| `_meta.modelVersion`    | `String` | Current model version |
| `_meta.states`          | `Object` | Current states        |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623955915055
Content-Disposition: inline;filename=f.txt
Content-Type: application/json;charset=UTF-8
Content-Length: 841

{
  "firstName" : "firstName1",
  "lastName" : "lastName1",
  "prefix" : "Mr.",
  "deathStatusCode" : 1,
  "statusReasonCode" : 1,
  "language" : "English",
  "type" : 1,
  "suffix" : "",
  "statusChangeDate" : 1623955914911,
  "partyState" : "NEW",
  "id" : 1,
  "birthDay" : 1623955914911,
  "status" : 1,
  "version" : 1,
  "_meta" : {
    "businessEntity" : "customer",
    "id" : {
      "sourceSystem" : "demo.system.default",
      "sourcePKey" : "c.1"
    },
    "createdBy" : "testUserName",
    "creationDate" : 1623955914951,
    "updatedBy" : "testUserName",
    "lastUpdateDate" : 1623955914951,
    "modelVersion" : "1",
    "states" : {
      "base" : "ACTIVE",
      "consolidation" : "MATCH_DIRTY",
      "searchIndex" : "SEARCH_DIRTY"
    },
    "businessId" : "29956699133795592794287015770",
    "xrefType" : "DATA"
  }
}
```

#### Delete XREF

##### Purpose

The Delete XREF API deletes the XREF record. The service integrates with the state management and soft deletes a record. The API sends a notification that the XREF Record is updated.

##### Sample Request

```http
DELETE /api/v1/entity-xref/customer/demo.system.default/c.1 HTTP/1.1
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `MODEL_VERSION`  | Model version  |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 204 No Content
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623955914654
```

### Batch

#### Batch Partition

##### Purpose

Split the documents inside the data source collections into small chunks. This is an asynchronous API. Will immediately send a 202 response. Once the work is done, it will send the result of the operation by send a POST request to the callback URL.

##### Sample Request

```http
POST /api/v1/batch/partition HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X_INFA_LOG_CTX: correlationID
X-INFA-ORG-ID: orgID
Host: business-entity
Content-Length: 93

{
  "jobInstanceId" : "jobInstanceId100",
  "callbackURL" : "https://cai:8787/cai/callback"
}
```

##### Request Headers

| Name             | Description               |
| :--------------- | :------------------------ |
| `IDS-SESSION-ID` | User login session ID     |
| `X_INFA_LOG_CTX` | Correlation ID (Optional) |

##### Request Fields

| Path            | Type     | Description     |
| :-------------- | :------- | :-------------- |
| `jobInstanceId` | `String` | Job Instance ID |
| `callbackURL`   | `String` | Callback URL    |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 202 Accepted
X_INFA_LOG_CTX: correlationID
```

#### Batch Load

##### Purpose

Upsert or delete entities that are stored in the data source collection. This is an asynchronous API. Will immediately send a 202 response. Once the work is done, it will send the result of the operation by send a POST request to the callback URL.

##### Sample Request

```http
POST /api/v1/batch/load HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X_INFA_LOG_CTX: correlationID
X-INFA-ORG-ID: orgID
Host: business-entity
Content-Length: 112

{
  "jobInstanceId" : "jobInstanceId100",
  "partition" : 1,
  "callbackURL" : "https://cai:8787/cai/callback"
}
```

##### Request Headers

| Name             | Description               |
| :--------------- | :------------------------ |
| `IDS-SESSION-ID` | User login session ID     |
| `X_INFA_LOG_CTX` | Correlation ID (Optional) |

##### Request Fields

| Path            | Type     | Description     |
| :-------------- | :------- | :-------------- |
| `jobInstanceId` | `String` | Job Instance ID |
| `partition`     | `Number` | Partition       |
| `callbackURL`   | `String` | Callback URL    |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 202 Accepted
X_INFA_LOG_CTX: correlationID
```

#### Batch V2 Load

##### Purpose

Upsert or delete entities that are stored in the data source collection. This is an asynchronous API. Will immediately send a 202 response. Once the work is done, it will send the result of the operation by send a POST request to the callback URL.

##### Sample Request

```http
POST /api/v2/batch/load HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X_INFA_LOG_CTX: correlationID
X-INFA-ORG-ID: orgID
Host: business-entity
Content-Length: 93

{
  "jobInstanceId" : "jobInstanceId110",
  "callbackURL" : "https://cai:8787/cai/callback"
}
```

##### Request Headers

| Name             | Description               |
| :--------------- | :------------------------ |
| `IDS-SESSION-ID` | User login session ID     |
| `X_INFA_LOG_CTX` | Correlation ID (Optional) |

##### Request Fields

| Path            | Type     | Description     |
| :-------------- | :------- | :-------------- |
| `jobInstanceId` | `String` | Job Instance ID |
| `callbackURL`   | `String` | Callback URL    |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 202 Accepted
X_INFA_LOG_CTX: correlationID
```

#### Batch Cleanup Job Resources

##### Purpose

Drop all temporary collections created by BE service for the given Job Instance ID. This is an asynchronous API. Will immediately send a 202 response. Once the work is done, it will send the result of the operation by send a POST request to the callback URL.

##### Sample Request

```http
POST /api/v1/cleanupJobResources HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X_INFA_LOG_CTX: correlationID
X-INFA-ORG-ID: orgID
Host: business-entity
Content-Length: 93

{
  "jobInstanceId" : "jobInstanceId100",
  "callbackURL" : "https://cai:8787/cai/callback"
}
```

##### Request Headers

| Name             | Description               |
| :--------------- | :------------------------ |
| `IDS-SESSION-ID` | User login session ID     |
| `X_INFA_LOG_CTX` | Correlation ID (Optional) |

##### Request Fields

| Path            | Type     | Description     |
| :-------------- | :------- | :-------------- |
| `jobInstanceId` | `String` | Job Instance ID |
| `callbackURL`   | `String` | Callback URL    |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 202 Accepted
X_INFA_LOG_CTX: correlationID
```

### MDM-CAI Flow

#### Physical Validation

##### Purpose

Create essential physical resources related to business entity (collections, indices) once a entity is CREATED/UPDATED/DELETED in metadata service. This is a synchronous API triggered by CAI flow.

##### Sample Request

```http
POST /api/v1/physicalValidation HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X_INFA_LOG_CTX: correlationID
X-INFA-ORG-ID: orgID
Host: business-entity
Content-Length: 2198

{
  "modelVersion" : "1624819783011",
  "changes" : [ {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@businessEntity[guid='customer']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  }, {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@businessEntity[guid='dealership']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  }, {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@businessEntity[guid='household']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  }, {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@businessEntity[guid='BEWithNoMatchConfig']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  }, {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@businessEntity[guid='gender']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  }, {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@businessEntity[guid='maritalStatus']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  }, {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@businessEntity[guid='qualified']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  }, {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@businessEntity[guid='age']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  }, {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@businessEntity[guid='country']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  }, {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@businessEntity[guid='state']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  }, {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@relationship[guid='DealershipToCustomer_ExistingCustomer']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  }, {
    "changeType" : "CREATE",
    "versionNumber" : 1,
    "referencePath" : "//@relationship[guid='CustomerToHousehold_MemberOf']",
    "frsId" : null,
    "metadataDependencies" : [ ]
  } ]
}
```

##### Request Headers

| Name             | Description                    |
| :--------------- | :----------------------------- |
| `CONTENT-TYPE`   | application/json;charset=UTF-8 |
| `IDS-SESSION-ID` | User Session ID                |
| `X-INFA-ORG-ID`  | Org ID                         |
| `X_INFA_LOG_CTX` | Correlation ID                 |

##### Request Fields

| Path                       | Type     | Description                                                  |
| :------------------------- | :------- | :----------------------------------------------------------- |
| `modelVersion`             | `String` | Global org model version. e.g. 12345689897                   |
| `changes`                  | `Array`  | Changes of metadata                                          |
| `changes[0].changeType`    | `String` | The type of the change, CREATE/UPDATE/DELETE                 |
| `changes[0].versionNumber` | `Number` | Integer indicating a version number of the metadata object within the model, e.g. 56 |
| `changes[0].referencePath` | `String` | EMF path to the metadata element, e.g. //@businessEntity[guid='be_customer'] |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `MODEL_VERSION`  | Model version  |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 201 Created
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1624819783011
```

#### Persist

##### Purpose

Accepts an array of operations which gets routed to the appropriate API implementation. All changes will be in one transaction. This is a synchronous API triggered by CAI flow.

##### Sample Request

```http
POST /api/v1/persist HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X-INFA-ORG-ID: orgID
X_INFA_LOG_CTX: correlationID
Host: business-entity
Content-Length: 752

{
  "application" : "",
  "changeListId" : "",
  "operations" : [ {
    "method" : "create",
    "resource" : "entity",
    "entityGuid" : "customer",
    "sourceSystem" : "HR",
    "sourcePKey" : "pk01",
    "internalId" : null,
    "payload" : {
      "firstName" : "firstName1",
      "lastName" : "lastName1",
      "middleName" : "middleName1",
      "prefix" : "Mr.",
      "deathStatusCode" : 3,
      "deathInd" : false,
      "statusReasonCode" : 74,
      "language" : "English",
      "type" : 9,
      "suffix" : "",
      "statusChangeDate" : 1485536218123,
      "state" : "NEW",
      "id" : 1,
      "birthDay" : "2001-01-01",
      "status" : 2,
      "housePrice" : "123.45",
      "salary" : 123.45,
      "version" : 5
    }
  } ]
}
```

##### Request Headers

| Name             | Description            |
| :--------------- | :--------------------- |
| `IDS-SESSION-ID` | User Session ID        |
| `X-INFA-ORG-ID`  | Org ID                 |
| `X_INFA_LOG_CTX` | Correlation ID         |
| `MODEL_VERSION`  | Metadata Model Version |

##### Request Fields

| Path           | Type     | Description         |
| :------------- | :------- | :------------------ |
| `application`  | `String` | Application context |
| `changeListId` | `String` | Change List ID      |
| `operations`   | `Array`  | Array of operation  |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `MODEL_VERSION`  | Model version  |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956942271
Content-Type: application/json;charset=UTF-8
Content-Length: 2271

{
  "approvalRequired" : false,
  "persistedAsActive" : true,
  "changeListId" : "",
  "messages" : {
    "records" : [ {
      "messageType" : "record_created",
      "entityType" : "BusinessEntity",
      "props" : {
        "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
        "name" : "customer"
      },
      "_meta" : {
        "createdBy" : "testUserName",
        "creationDate" : 1623956942250,
        "updatedBy" : "testUserName",
        "lastUpdateDate" : 1623956942250,
        "modelVersion" : "2",
        "states" : {
          "base" : "ACTIVE",
          "consolidation" : "MATCH_DIRTY",
          "searchIndex" : "SEARCH_DIRTY"
        },
        "businessId" : "29956718097048500567706083900",
        "changeList" : null,
        "status" : "ACTIVE",
        "type" : "customer",
        "jobId" : null
      },
      "_system" : {
        "storageVersion" : 2,
        "recordVersion" : 1
      }
    } ],
    "xrefs" : [ {
      "messageType" : "xref_created",
      "entityType" : "BusinessEntity",
      "props" : {
        "sourceSystem" : "HR",
        "sourcePKey" : "pk01",
        "name" : "customer"
      },
      "_meta" : {
        "createdBy" : "testUserName",
        "creationDate" : 1623956942250,
        "updatedBy" : "testUserName",
        "lastUpdateDate" : 1623956942250,
        "modelVersion" : "2",
        "states" : {
          "base" : "ACTIVE",
          "consolidation" : "MATCH_DIRTY",
          "searchIndex" : "SEARCH_DIRTY"
        },
        "changeList" : null,
        "businessId" : "29956718097048500567706083900",
        "xrefType" : "DATA",
        "type" : "customer",
        "jobId" : null
      },
      "_system" : {
        "storageVersion" : 2,
        "recordVersion" : 1
      }
    } ],
    "groups" : [ {
      "messageType" : "group_created",
      "entityType" : "BusinessEntity",
      "props" : {
        "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
        "name" : "customer"
      },
      "payload" : {
        "created" : {
          "businessEntity" : "customer",
          "id" : "1aaaaaaaaaaaaaaaaaaaaaaa"
        },
        "from" : [ {
          "businessEntity" : "customer",
          "sourceSystem" : "HR",
          "sourcePKey" : "pk01"
        } ]
      }
    } ],
    "validations" : [ ]
  }
}
```

### Read History

#### Purpose

Retrieve a single history record.

#### Sample Request

```http
GET /api/v1/history/BE/customer/60cb9c3db1ffd9f650602d15 HTTP/1.1
Host: business-entity
```

#### Path parameters

| Parameter    | Description       |
| :----------- | :---------------- |
| `entityType` | Entity type       |
| `entityName` | Entity name       |
| `id`         | History record ID |

#### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: 61b01f48-39ac-4df1-b0e8-9c03bbc08256
MODEL_VERSION: 1623956541577
Content-Type: application/json;charset=UTF-8
Content-Length: 7267

{
  "_id" : "60cb9c3db1ffd9f650602d15",
  "entityName" : "customer",
  "changedAttributes" : [ {
    "attribute" : "$.payload._cm.trust.fieldData[0].fieldRef",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "/"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].lud",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956541531
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].mo",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : false
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].pKey",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "2aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].system",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "demo.system.default"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].tr",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "Decay"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].ts",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 0.9
  }, {
    "attribute" : "$.payload._meta.businessEntity",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.payload._meta.businessId",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "29956710699904127010175883976"
  }, {
    "attribute" : "$.payload._meta.createdBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload._meta.creationDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956541531
  }, {
    "attribute" : "$.payload._meta.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.payload._meta.lastUpdateDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956541531
  }, {
    "attribute" : "$.payload._meta.modelVersion",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1"
  }, {
    "attribute" : "$.payload._meta.states.base",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "ACTIVE"
  }, {
    "attribute" : "$.payload._meta.states.consolidation",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "MATCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.states.searchIndex",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "SEARCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.status",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "ACTIVE"
  }, {
    "attribute" : "$.payload._meta.updatedBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload.birthDay",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "2001-01-01"
  }, {
    "attribute" : "$.payload.deathInd",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : false
  }, {
    "attribute" : "$.payload.deathStatusCode",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 3
  }, {
    "attribute" : "$.payload.firstName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "firstName1"
  }, {
    "attribute" : "$.payload.housePrice",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "123.45"
  }, {
    "attribute" : "$.payload.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1
  }, {
    "attribute" : "$.payload.language",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "English"
  }, {
    "attribute" : "$.payload.lastName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "lastName1"
  }, {
    "attribute" : "$.payload.middleName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "middleName1"
  }, {
    "attribute" : "$.payload.prefix",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "Mr."
  }, {
    "attribute" : "$.payload.salary",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 123.45
  }, {
    "attribute" : "$.payload.state",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "NEW"
  }, {
    "attribute" : "$.payload.status",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 2
  }, {
    "attribute" : "$.payload.statusChangeDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1485536218123
  }, {
    "attribute" : "$.payload.statusReasonCode",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 74
  }, {
    "attribute" : "$.payload.suffix",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : ""
  }, {
    "attribute" : "$.payload.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 9
  }, {
    "attribute" : "$.payload.version",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 5
  }, {
    "attribute" : "$.props.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.props.name",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "BusinessEntity"
  } ],
  "value" : {
    "type" : "BusinessEntity",
    "props" : {
      "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
      "name" : "customer"
    },
    "payload" : {
      "firstName" : "firstName1",
      "lastName" : "lastName1",
      "middleName" : "middleName1",
      "prefix" : "Mr.",
      "deathStatusCode" : 3,
      "deathInd" : false,
      "statusReasonCode" : 74,
      "language" : "English",
      "type" : 9,
      "suffix" : "",
      "statusChangeDate" : 1485536218123,
      "state" : "NEW",
      "id" : 1,
      "birthDay" : "2001-01-01",
      "status" : 2,
      "housePrice" : "123.45",
      "salary" : 123.45,
      "version" : 5,
      "_meta" : {
        "businessEntity" : "customer",
        "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
        "createdBy" : "testUserName",
        "creationDate" : 1623956541531,
        "updatedBy" : "testUserName",
        "lastUpdateDate" : 1623956541531,
        "modelVersion" : "1",
        "states" : {
          "base" : "ACTIVE",
          "consolidation" : "MATCH_DIRTY",
          "searchIndex" : "SEARCH_DIRTY"
        },
        "businessId" : "29956710699904127010175883976",
        "status" : "ACTIVE"
      },
      "_cm" : {
        "trust" : {
          "fieldData" : [ {
            "fieldRef" : "/",
            "lud" : 1623956541531,
            "system" : "demo.system.default",
            "pKey" : "2aaaaaaaaaaaaaaaaaaaaaaa",
            "tr" : "Decay",
            "ts" : 0.9,
            "mo" : false
          } ]
        },
        "match" : [ ]
      }
    }
  },
  "dataDomain" : null,
  "entityType" : "BE",
  "entityId" : "1aaaaaaaaaaaaaaaaaaaaaaa",
  "eventType" : "BusinessEntity.record_created",
  "eventTimestamp" : 1623956541531,
  "userId" : "testUserName",
  "applicationId" : "BusinessEntityService",
  "correlationId" : "f5fc9bce-3c8e-4e61-98b6-a6fd193b454b",
  "previousId" : null,
  "signature" : "-1828475411"
}
```

#### Response Fields

| Path                | Type     | Description        |
| :------------------ | :------- | :----------------- |
| `entityType`        | `String` | Entity type        |
| `entityName`        | `String` | Entity name        |
| `entityId`          | `String` | Entity ID          |
| `eventType`         | `String` | Event type         |
| `eventTimestamp`    | `Number` | Event timestamp    |
| `userId`            | `String` | User ID            |
| `applicationId`     | `String` | ApplicationID      |
| `correlationId`     | `String` | Correlation ID     |
| `value`             | `Object` | Value              |
| `changedAttributes` | `Array`  | Changed attributes |
| `signature`         | `String` | Signature          |
| `_id`               | `String` | ID                 |

### List History Without Filter

#### Purpose

Retrieve several history records.

#### Sample Request

```http
GET /api/v1/history/ HTTP/1.1
Host: business-entity
```

#### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: 83b6ed91-2516-456b-9681-be89b512732c
Content-Type: application/json;charset=UTF-8
Content-Length: 15167

[ {
  "_id" : "60cb9c3db1ffd9f650602e40",
  "entityName" : "customer",
  "changedAttributes" : [ {
    "attribute" : "$.payload._meta.createdBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload._meta.creationDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956541909
  }, {
    "attribute" : "$.payload._meta.editXref",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : false
  }, {
    "attribute" : "$.payload._meta.lastUpdateDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956541909
  }, {
    "attribute" : "$.payload._meta.modelVersion",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1"
  }, {
    "attribute" : "$.payload._meta.states.base",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "ACTIVE"
  }, {
    "attribute" : "$.payload._meta.states.consolidation",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "MATCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.states.searchIndex",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "SEARCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.payload._meta.updatedBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload.id.businessEntity",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.payload.id.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.payload.reason.matches[0].businessEntity",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.payload.reason.matches[0].id.sourcePKey",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "2aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.payload.reason.matches[0].id.sourceSystem",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "demo.system.default"
  }, {
    "attribute" : "$.props.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.props.name",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "BusinessEntity"
  } ],
  "value" : {
    "type" : "BusinessEntity",
    "props" : {
      "name" : "customer",
      "id" : "1aaaaaaaaaaaaaaaaaaaaaaa"
    },
    "payload" : {
      "id" : {
        "businessEntity" : "customer",
        "id" : "1aaaaaaaaaaaaaaaaaaaaaaa"
      },
      "reason" : {
        "matches" : [ {
          "businessEntity" : "customer",
          "id" : {
            "sourceSystem" : "demo.system.default",
            "sourcePKey" : "2aaaaaaaaaaaaaaaaaaaaaaa"
          }
        } ]
      },
      "_meta" : {
        "editXref" : false,
        "createdBy" : "testUserName",
        "creationDate" : 1623956541909,
        "updatedBy" : "testUserName",
        "lastUpdateDate" : 1623956541909,
        "modelVersion" : "1",
        "states" : {
          "base" : "ACTIVE",
          "consolidation" : "MATCH_DIRTY",
          "searchIndex" : "SEARCH_DIRTY"
        },
        "type" : "customer"
      }
    }
  },
  "dataDomain" : null,
  "entityType" : "BE-LINK",
  "entityId" : "1aaaaaaaaaaaaaaaaaaaaaaa",
  "eventType" : "BusinessEntity.link_created",
  "eventTimestamp" : 1623956541909,
  "userId" : "testUserName",
  "applicationId" : "BusinessEntityService",
  "correlationId" : "68201896-65ad-4a56-8eb9-47ffd9dbe7d1",
  "previousId" : null,
  "signature" : "-2074943101"
}, {
  "_id" : "60cb9c3db1ffd9f650602e42",
  "entityName" : "customer",
  "changedAttributes" : [ {
    "attribute" : "$.payload._meta.createdBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload._meta.creationDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956541909
  }, {
    "attribute" : "$.payload._meta.editXref",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : false
  }, {
    "attribute" : "$.payload._meta.lastUpdateDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956541909
  }, {
    "attribute" : "$.payload._meta.modelVersion",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1"
  }, {
    "attribute" : "$.payload._meta.states.base",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "ACTIVE"
  }, {
    "attribute" : "$.payload._meta.states.consolidation",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "MATCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.states.searchIndex",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "SEARCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.payload._meta.updatedBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload.id.businessEntity",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.payload.id.id.sourcePKey",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "2aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.payload.id.id.sourceSystem",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "demo.system.default"
  }, {
    "attribute" : "$.payload.parent.businessEntity",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.payload.parent.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.props.name",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.props.sourcePKey",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "2aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.props.sourceSystem",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "demo.system.default"
  }, {
    "attribute" : "$.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "BusinessEntity"
  } ],
  "value" : {
    "type" : "BusinessEntity",
    "props" : {
      "name" : "customer",
      "sourceSystem" : "demo.system.default",
      "sourcePKey" : "2aaaaaaaaaaaaaaaaaaaaaaa"
    },
    "payload" : {
      "id" : {
        "businessEntity" : "customer",
        "id" : {
          "sourceSystem" : "demo.system.default",
          "sourcePKey" : "2aaaaaaaaaaaaaaaaaaaaaaa"
        }
      },
      "parent" : {
        "businessEntity" : "customer",
        "id" : "1aaaaaaaaaaaaaaaaaaaaaaa"
      },
      "_meta" : {
        "editXref" : false,
        "createdBy" : "testUserName",
        "creationDate" : 1623956541909,
        "updatedBy" : "testUserName",
        "lastUpdateDate" : 1623956541909,
        "modelVersion" : "1",
        "states" : {
          "base" : "ACTIVE",
          "consolidation" : "MATCH_DIRTY",
          "searchIndex" : "SEARCH_DIRTY"
        },
        "type" : "customer"
      }
    }
  },
  "dataDomain" : null,
  "entityType" : "BE-LINK",
  "entityId" : "demo.system.default/2aaaaaaaaaaaaaaaaaaaaaaa",
  "eventType" : "BusinessEntity.link_created",
  "eventTimestamp" : 1623956541909,
  "userId" : "testUserName",
  "applicationId" : "BusinessEntityService",
  "correlationId" : "68201896-65ad-4a56-8eb9-47ffd9dbe7d1",
  "previousId" : null,
  "signature" : "-1546209430"
}, {
  "_id" : "60cb9c3db1ffd9f650602e44",
  "entityName" : "customer",
  "changedAttributes" : [ {
    "attribute" : "$.payload._cm.trust.fieldData[0].fieldRef",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "/"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].lud",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956541909
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].mo",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : false
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].pKey",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "2aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].system",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "demo.system.default"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].tr",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "Decay"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].ts",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 0.9
  }, {
    "attribute" : "$.payload._meta.businessEntity",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.payload._meta.businessId",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "29956710699904127010175883978"
  }, {
    "attribute" : "$.payload._meta.createdBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload._meta.creationDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956541909
  }, {
    "attribute" : "$.payload._meta.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.payload._meta.lastUpdateDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956541909
  }, {
    "attribute" : "$.payload._meta.modelVersion",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1"
  }, {
    "attribute" : "$.payload._meta.states.base",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "ACTIVE"
  }, {
    "attribute" : "$.payload._meta.states.consolidation",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "MATCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.states.searchIndex",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "SEARCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.status",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "ACTIVE"
  }, {
    "attribute" : "$.payload._meta.updatedBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload.birthDay",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "2001-01-01"
  }, {
    "attribute" : "$.payload.deathInd",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : false
  }, {
    "attribute" : "$.payload.deathStatusCode",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 3
  }, {
    "attribute" : "$.payload.firstName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "firstName1"
  }, {
    "attribute" : "$.payload.housePrice",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "123.45"
  }, {
    "attribute" : "$.payload.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1
  }, {
    "attribute" : "$.payload.language",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "English"
  }, {
    "attribute" : "$.payload.lastName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "lastName1"
  }, {
    "attribute" : "$.payload.middleName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "middleName1"
  }, {
    "attribute" : "$.payload.prefix",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "Mr."
  }, {
    "attribute" : "$.payload.salary",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 123.45
  }, {
    "attribute" : "$.payload.state",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "NEW"
  }, {
    "attribute" : "$.payload.status",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 2
  }, {
    "attribute" : "$.payload.statusChangeDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1485536218123
  }, {
    "attribute" : "$.payload.statusReasonCode",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 74
  }, {
    "attribute" : "$.payload.suffix",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : ""
  }, {
    "attribute" : "$.payload.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 9
  }, {
    "attribute" : "$.payload.version",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 5
  }, {
    "attribute" : "$.props.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.props.name",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "BusinessEntity"
  } ],
  "value" : {
    "type" : "BusinessEntity",
    "props" : {
      "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
      "name" : "customer"
    },
    "payload" : {
      "firstName" : "firstName1",
      "lastName" : "lastName1",
      "middleName" : "middleName1",
      "prefix" : "Mr.",
      "deathStatusCode" : 3,
      "deathInd" : false,
      "statusReasonCode" : 74,
      "language" : "English",
      "type" : 9,
      "suffix" : "",
      "statusChangeDate" : 1485536218123,
      "state" : "NEW",
      "id" : 1,
      "birthDay" : "2001-01-01",
      "status" : 2,
      "housePrice" : "123.45",
      "salary" : 123.45,
      "version" : 5,
      "_meta" : {
        "businessEntity" : "customer",
        "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
        "createdBy" : "testUserName",
        "creationDate" : 1623956541909,
        "updatedBy" : "testUserName",
        "lastUpdateDate" : 1623956541909,
        "modelVersion" : "1",
        "states" : {
          "base" : "ACTIVE",
          "consolidation" : "MATCH_DIRTY",
          "searchIndex" : "SEARCH_DIRTY"
        },
        "businessId" : "29956710699904127010175883978",
        "status" : "ACTIVE"
      },
      "_cm" : {
        "trust" : {
          "fieldData" : [ {
            "fieldRef" : "/",
            "lud" : 1623956541909,
            "system" : "demo.system.default",
            "pKey" : "2aaaaaaaaaaaaaaaaaaaaaaa",
            "tr" : "Decay",
            "ts" : 0.9,
            "mo" : false
          } ]
        },
        "match" : [ ]
      }
    }
  },
  "dataDomain" : null,
  "entityType" : "BE",
  "entityId" : "1aaaaaaaaaaaaaaaaaaaaaaa",
  "eventType" : "BusinessEntity.record_created",
  "eventTimestamp" : 1623956541909,
  "userId" : "testUserName",
  "applicationId" : "BusinessEntityService",
  "correlationId" : "68201896-65ad-4a56-8eb9-47ffd9dbe7d1",
  "previousId" : null,
  "signature" : "-1828475495"
} ]
```

#### Response Fields

| Path                   | Type     | Description              |
| :--------------------- | :------- | :----------------------- |
| `[]`                   | `Array`  | Array of history records |
| `[].entityType`        | `String` | Entity type              |
| `[].entityName`        | `String` | Entity name              |
| `[].entityId`          | `String` | Entity ID                |
| `[].eventType`         | `String` | Event type               |
| `[].eventTimestamp`    | `Number` | Event timestamp          |
| `[].userId`            | `String` | User ID                  |
| `[].applicationId`     | `String` | ApplicationID            |
| `[].correlationId`     | `String` | Correlation ID           |
| `[].value`             | `Object` | Value                    |
| `[].changedAttributes` | `Array`  | Changed attributes       |
| `[].signature`         | `String` | Signature                |
| `[]._id`               | `String` | ID                       |

### List History With Filter Parameters

#### Purpose

Retrieve several history records that satisfies the filter.

#### Sample Request

```http
GET /api/v1/history/?_filter=%7B_and:%20%5B%7BentityType:%20%22BE%22%7D,%20%7BentityName:%20%22customer%22%7D%5D%7D HTTP/1.1
Host: business-entity
```

#### Request parameters

| Parameter | Description |
| :-------- | :---------- |
| `_filter` | Filter      |

#### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: e0a68d89-7cf5-436b-ba17-867a86629217
Content-Type: application/json;charset=UTF-8
Content-Length: 7270

[ {
  "_id" : "60cb9c3cb1ffd9f650602969",
  "entityName" : "customer",
  "changedAttributes" : [ {
    "attribute" : "$.payload._cm.trust.fieldData[0].fieldRef",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "/"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].lud",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956540055
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].mo",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : false
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].pKey",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "2aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].system",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "demo.system.default"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].tr",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "Decay"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].ts",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 0.9
  }, {
    "attribute" : "$.payload._meta.businessEntity",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.payload._meta.businessId",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "29956710681457382936466332350"
  }, {
    "attribute" : "$.payload._meta.createdBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload._meta.creationDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956540055
  }, {
    "attribute" : "$.payload._meta.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.payload._meta.lastUpdateDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956540055
  }, {
    "attribute" : "$.payload._meta.modelVersion",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1"
  }, {
    "attribute" : "$.payload._meta.states.base",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "ACTIVE"
  }, {
    "attribute" : "$.payload._meta.states.consolidation",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "MATCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.states.searchIndex",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "SEARCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.status",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "ACTIVE"
  }, {
    "attribute" : "$.payload._meta.updatedBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload.birthDay",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "2001-01-01"
  }, {
    "attribute" : "$.payload.deathInd",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : false
  }, {
    "attribute" : "$.payload.deathStatusCode",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 3
  }, {
    "attribute" : "$.payload.firstName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "firstName1"
  }, {
    "attribute" : "$.payload.housePrice",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "123.45"
  }, {
    "attribute" : "$.payload.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1
  }, {
    "attribute" : "$.payload.language",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "English"
  }, {
    "attribute" : "$.payload.lastName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "lastName1"
  }, {
    "attribute" : "$.payload.middleName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "middleName1"
  }, {
    "attribute" : "$.payload.prefix",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "Mr."
  }, {
    "attribute" : "$.payload.salary",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 123.45
  }, {
    "attribute" : "$.payload.state",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "NEW"
  }, {
    "attribute" : "$.payload.status",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 2
  }, {
    "attribute" : "$.payload.statusChangeDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1485536218123
  }, {
    "attribute" : "$.payload.statusReasonCode",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 74
  }, {
    "attribute" : "$.payload.suffix",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : ""
  }, {
    "attribute" : "$.payload.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 9
  }, {
    "attribute" : "$.payload.version",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 5
  }, {
    "attribute" : "$.props.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.props.name",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "BusinessEntity"
  } ],
  "value" : {
    "type" : "BusinessEntity",
    "props" : {
      "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
      "name" : "customer"
    },
    "payload" : {
      "firstName" : "firstName1",
      "lastName" : "lastName1",
      "middleName" : "middleName1",
      "prefix" : "Mr.",
      "deathStatusCode" : 3,
      "deathInd" : false,
      "statusReasonCode" : 74,
      "language" : "English",
      "type" : 9,
      "suffix" : "",
      "statusChangeDate" : 1485536218123,
      "state" : "NEW",
      "id" : 1,
      "birthDay" : "2001-01-01",
      "status" : 2,
      "housePrice" : "123.45",
      "salary" : 123.45,
      "version" : 5,
      "_meta" : {
        "businessEntity" : "customer",
        "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
        "createdBy" : "testUserName",
        "creationDate" : 1623956540055,
        "updatedBy" : "testUserName",
        "lastUpdateDate" : 1623956540055,
        "modelVersion" : "1",
        "states" : {
          "base" : "ACTIVE",
          "consolidation" : "MATCH_DIRTY",
          "searchIndex" : "SEARCH_DIRTY"
        },
        "businessId" : "29956710681457382936466332350",
        "status" : "ACTIVE"
      },
      "_cm" : {
        "trust" : {
          "fieldData" : [ {
            "fieldRef" : "/",
            "lud" : 1623956540055,
            "system" : "demo.system.default",
            "pKey" : "2aaaaaaaaaaaaaaaaaaaaaaa",
            "tr" : "Decay",
            "ts" : 0.9,
            "mo" : false
          } ]
        },
        "match" : [ ]
      }
    }
  },
  "dataDomain" : null,
  "entityType" : "BE",
  "entityId" : "1aaaaaaaaaaaaaaaaaaaaaaa",
  "eventType" : "BusinessEntity.record_created",
  "eventTimestamp" : 1623956540055,
  "userId" : "testUserName",
  "applicationId" : "BusinessEntityService",
  "correlationId" : "2911c276-440e-49ac-99ba-1adf70bf20bd",
  "previousId" : null,
  "signature" : "-847374089"
} ]
```

#### Response Fields

| Path                   | Type     | Description              |
| :--------------------- | :------- | :----------------------- |
| `[]`                   | `Array`  | Array of history records |
| `[].entityType`        | `String` | Entity type              |
| `[].entityName`        | `String` | Entity name              |
| `[].entityId`          | `String` | Entity ID                |
| `[].eventType`         | `String` | Event type               |
| `[].eventTimestamp`    | `Number` | Event timestamp          |
| `[].userId`            | `String` | User ID                  |
| `[].applicationId`     | `String` | ApplicationID            |
| `[].correlationId`     | `String` | Correlation ID           |
| `[].value`             | `Object` | Value                    |
| `[].changedAttributes` | `Array`  | Changed attributes       |
| `[].signature`         | `String` | Signature                |
| `[]._id`               | `String` | ID                       |

### List History With Filter Payload

#### Purpose

Retrieve several history records that satisfies the filter.

#### Sample Request

```http
POST /api/v1/history/ HTTP/1.1
Content-Type: application/json;charset=UTF-8
Host: business-entity
Content-Length: 115

{
  "_filter" : {
    "_and" : [ {
      "entityType" : "BE"
    }, {
      "entityName" : "customer"
    } ]
  }
}
```

#### Request Fields

| Path      | Type     | Description |
| :-------- | :------- | :---------- |
| `_filter` | `Object` | Filter      |

#### Sample Response

```http
HTTP/1.1 200 OK
X_INFA_LOG_CTX: 75c952d1-1bb0-4f97-a201-abb4b04b8239
Content-Type: application/json;charset=UTF-8
Content-Length: 7270

[ {
  "_id" : "60cb9c3eb1ffd9f6506030fa",
  "entityName" : "customer",
  "changedAttributes" : [ {
    "attribute" : "$.payload._cm.trust.fieldData[0].fieldRef",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "/"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].lud",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956542866
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].mo",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : false
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].pKey",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "2aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].system",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "demo.system.default"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].tr",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "Decay"
  }, {
    "attribute" : "$.payload._cm.trust.fieldData[0].ts",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 0.9
  }, {
    "attribute" : "$.payload._meta.businessEntity",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.payload._meta.businessId",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "29956710718350871083885435599"
  }, {
    "attribute" : "$.payload._meta.createdBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload._meta.creationDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956542866
  }, {
    "attribute" : "$.payload._meta.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.payload._meta.lastUpdateDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1623956542866
  }, {
    "attribute" : "$.payload._meta.modelVersion",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1"
  }, {
    "attribute" : "$.payload._meta.states.base",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "ACTIVE"
  }, {
    "attribute" : "$.payload._meta.states.consolidation",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "MATCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.states.searchIndex",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "SEARCH_DIRTY"
  }, {
    "attribute" : "$.payload._meta.status",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "ACTIVE"
  }, {
    "attribute" : "$.payload._meta.updatedBy",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "testUserName"
  }, {
    "attribute" : "$.payload.birthDay",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "2001-01-01"
  }, {
    "attribute" : "$.payload.deathInd",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : false
  }, {
    "attribute" : "$.payload.deathStatusCode",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 3
  }, {
    "attribute" : "$.payload.firstName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "firstName1"
  }, {
    "attribute" : "$.payload.housePrice",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "123.45"
  }, {
    "attribute" : "$.payload.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1
  }, {
    "attribute" : "$.payload.language",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "English"
  }, {
    "attribute" : "$.payload.lastName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "lastName1"
  }, {
    "attribute" : "$.payload.middleName",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "middleName1"
  }, {
    "attribute" : "$.payload.prefix",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "Mr."
  }, {
    "attribute" : "$.payload.salary",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 123.45
  }, {
    "attribute" : "$.payload.state",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "NEW"
  }, {
    "attribute" : "$.payload.status",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 2
  }, {
    "attribute" : "$.payload.statusChangeDate",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 1485536218123
  }, {
    "attribute" : "$.payload.statusReasonCode",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 74
  }, {
    "attribute" : "$.payload.suffix",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : ""
  }, {
    "attribute" : "$.payload.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 9
  }, {
    "attribute" : "$.payload.version",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : 5
  }, {
    "attribute" : "$.props.id",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "1aaaaaaaaaaaaaaaaaaaaaaa"
  }, {
    "attribute" : "$.props.name",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "customer"
  }, {
    "attribute" : "$.type",
    "operation" : "N",
    "previousValue" : null,
    "newValue" : "BusinessEntity"
  } ],
  "value" : {
    "type" : "BusinessEntity",
    "props" : {
      "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
      "name" : "customer"
    },
    "payload" : {
      "firstName" : "firstName1",
      "lastName" : "lastName1",
      "middleName" : "middleName1",
      "prefix" : "Mr.",
      "deathStatusCode" : 3,
      "deathInd" : false,
      "statusReasonCode" : 74,
      "language" : "English",
      "type" : 9,
      "suffix" : "",
      "statusChangeDate" : 1485536218123,
      "state" : "NEW",
      "id" : 1,
      "birthDay" : "2001-01-01",
      "status" : 2,
      "housePrice" : "123.45",
      "salary" : 123.45,
      "version" : 5,
      "_meta" : {
        "businessEntity" : "customer",
        "id" : "1aaaaaaaaaaaaaaaaaaaaaaa",
        "createdBy" : "testUserName",
        "creationDate" : 1623956542866,
        "updatedBy" : "testUserName",
        "lastUpdateDate" : 1623956542866,
        "modelVersion" : "1",
        "states" : {
          "base" : "ACTIVE",
          "consolidation" : "MATCH_DIRTY",
          "searchIndex" : "SEARCH_DIRTY"
        },
        "businessId" : "29956710718350871083885435599",
        "status" : "ACTIVE"
      },
      "_cm" : {
        "trust" : {
          "fieldData" : [ {
            "fieldRef" : "/",
            "lud" : 1623956542866,
            "system" : "demo.system.default",
            "pKey" : "2aaaaaaaaaaaaaaaaaaaaaaa",
            "tr" : "Decay",
            "ts" : 0.9,
            "mo" : false
          } ]
        },
        "match" : [ ]
      }
    }
  },
  "dataDomain" : null,
  "entityType" : "BE",
  "entityId" : "1aaaaaaaaaaaaaaaaaaaaaaa",
  "eventType" : "BusinessEntity.record_created",
  "eventTimestamp" : 1623956542866,
  "userId" : "testUserName",
  "applicationId" : "BusinessEntityService",
  "correlationId" : "314a1582-cf8f-40c0-847a-59485096ce21",
  "previousId" : null,
  "signature" : "-374713021"
} ]
```

#### Response Fields

| Path                   | Type     | Description              |
| :--------------------- | :------- | :----------------------- |
| `[]`                   | `Array`  | Array of history records |
| `[].entityType`        | `String` | Entity type              |
| `[].entityName`        | `String` | Entity name              |
| `[].entityId`          | `String` | Entity ID                |
| `[].eventType`         | `String` | Event type               |
| `[].eventTimestamp`    | `Number` | Event timestamp          |
| `[].userId`            | `String` | User ID                  |
| `[].applicationId`     | `String` | ApplicationID            |
| `[].correlationId`     | `String` | Correlation ID           |
| `[].value`             | `Object` | Value                    |
| `[].changedAttributes` | `Array`  | Changed attributes       |
| `[].signature`         | `String` | Signature                |
| `[]._id`               | `String` | ID                       |

### Trust Overrides

#### Add or update trust override on master record by internal id.

##### Purpose

Add or update trust override on master record by internal id.

##### Path parameters

| Parameter    | Description |
| :----------- | :---------- |
| `entityType` | Entity type |
| `entityName` | Entity name |
| `internalId` | Internal ID |

##### Sample Request

```http
PUT /api/v1/entity/be_decay/1aaaaaaaaaaaaaaaaaaaaaaa/content-metadata/trust HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X_INFA_LOG_CTX: correlationID
X-INFA-ORG-ID: orgID
Host: business-entity
Content-Length: 90

[ {
  "fieldRef" : "firstName",
  "system" : "system1",
  "pKey" : "pk1",
  "ts" : 1.0
} ]
```

##### Request Headers

| Name             | Description               |
| :--------------- | :------------------------ |
| `IDS-SESSION-ID` | User login session ID     |
| `X_INFA_LOG_CTX` | Correlation ID (Optional) |

##### Request Fields

| Path          | Type     | Description              |
| :------------ | :------- | :----------------------- |
| `[]`          | `Array`  | Array of trust overrides |
| `[].fieldRef` | `String` | Field reference path     |
| `[].system`   | `String` | Source system            |
| `[].pKey`     | `String` | Source primary key       |
| `[].ts`       | `Number` | Trust score              |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 204 No Content
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956554599
```

#### Add or update trust override on master record by business id.

##### Purpose

Add or update trust override on master record by business id.

##### Path parameters

| Parameter    | Description |
| :----------- | :---------- |
| `entityType` | Entity type |
| `entityName` | Entity name |
| `businessId` | Business ID |

##### Sample Request

```http
PUT /api/v1/entity/be_decay/business-id/29956710921265055894690503433/content-metadata/trust HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X_INFA_LOG_CTX: correlationID
X-INFA-ORG-ID: orgID
Host: business-entity
Content-Length: 90

[ {
  "fieldRef" : "firstName",
  "system" : "system1",
  "pKey" : "pk1",
  "ts" : 1.0
} ]
```

##### Request Headers

| Name             | Description               |
| :--------------- | :------------------------ |
| `IDS-SESSION-ID` | User login session ID     |
| `X_INFA_LOG_CTX` | Correlation ID (Optional) |

##### Request Fields

| Path          | Type     | Description              |
| :------------ | :------- | :----------------------- |
| `[]`          | `Array`  | Array of trust overrides |
| `[].fieldRef` | `String` | Field reference path     |
| `[].system`   | `String` | Source system            |
| `[].pKey`     | `String` | Source primary key       |
| `[].ts`       | `Number` | Trust score              |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 204 No Content
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956553781
```

#### Delete trust override on master record by internal id.

##### Purpose

Delete trust override on master record by internal id.

##### Path parameters

| Parameter    | Description |
| :----------- | :---------- |
| `entityType` | Entity type |
| `entityName` | Entity name |
| `internalId` | Internal ID |

##### Sample Request

```http
PUT /api/v1/entity/be_decay/1aaaaaaaaaaaaaaaaaaaaaaa/content-metadata/trust HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X_INFA_LOG_CTX: correlationID
X-INFA-ORG-ID: orgID
Host: business-entity
Content-Length: 50

[ {
  "fieldRef" : "firstName",
  "mo" : false
} ]
```

##### Request Headers

| Name             | Description               |
| :--------------- | :------------------------ |
| `IDS-SESSION-ID` | User login session ID     |
| `X_INFA_LOG_CTX` | Correlation ID (Optional) |

##### Request Fields

| Path          | Type      | Description               |
| :------------ | :-------- | :------------------------ |
| `[]`          | `Array`   | Array of trust overrides  |
| `[].fieldRef` | `String`  | Field reference path      |
| `[].mo`       | `Boolean` | Manual override indicator |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 204 No Content
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956554228
```

#### Delete trust override on master record by business id.

##### Purpose

Delete trust override on master record by business id.

##### Path parameters

| Parameter    | Description |
| :----------- | :---------- |
| `entityType` | Entity type |
| `entityName` | Entity name |
| `businessId` | Business ID |

##### Sample Request

```http
PUT /api/v1/entity/be_decay/business-id/29956710958158544042109606671/content-metadata/trust HTTP/1.1
Content-Type: application/json;charset=UTF-8
IDS-SESSION-ID: sessionID
X_INFA_LOG_CTX: correlationID
X-INFA-ORG-ID: orgID
Host: business-entity
Content-Length: 50

[ {
  "fieldRef" : "firstName",
  "mo" : false
} ]
```

##### Request Headers

| Name             | Description               |
| :--------------- | :------------------------ |
| `IDS-SESSION-ID` | User login session ID     |
| `X_INFA_LOG_CTX` | Correlation ID (Optional) |

##### Request Fields

| Path          | Type      | Description               |
| :------------ | :-------- | :------------------------ |
| `[]`          | `Array`   | Array of trust overrides  |
| `[].fieldRef` | `String`  | Field reference path      |
| `[].mo`       | `Boolean` | Manual override indicator |

##### Response Headers

| Name             | Description    |
| :--------------- | :------------- |
| `X_INFA_LOG_CTX` | Correlation ID |

##### Sample Response

```http
HTTP/1.1 204 No Content
X_INFA_LOG_CTX: correlationID
MODEL_VERSION: 1623956555730
```