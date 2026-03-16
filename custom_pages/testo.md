---
title: Testo
fullscreen: false
hidden: true
metadata:
  title: ''
  description: ''
---
This document provides feature descriptions and technical information about Prove’s latest release. As you plan your implementation or upgrades of new API features, remember that Prove’s Support team is always here to help.

**Release Dates**  
**Staging: **Tuesday, July 25th, 2023, at 3 PM MST  
**Production:** Tuesday, August 1st, 2023, at 11 PM MST

## Growth

The following describes growth opportunities that were added in this release.

### 1. IDP-[2203](https://payfone.jira.com/browse/IDP-2203): Identity Verify Two Authoritative Sources - CIP+

In order to allow clients to be in compliance with the regulations set for DDA accounts, the data submitted in the Identity Verify request needs to be run against multiple authoritative data sources. Prove's solution to this is referred to as CIP+.

The Identity Verify response will include the Identity Verify payload from both data sources (Tdata and Idata will initially be configured). Each data source response should include the `verified`, `address` (`streetNumber`, `street`, `city`, `region`, `postalCode`, `distance`, `addressScore`), `name` (`firstName`, `lastName`, `nameScore`), `identifiers` (`last4`, `fullSSN`, `dob`, `driversLicenseState`, `driversLicenseNumber`), `email` (`emailAddress`) and `reasonCodes` response parameters if the request includes the necessary information for each parameter.

The Identity Verify response has been updated to include a new parameter for the verified decision (labeled `multiVerify`) that combines the verified response parameters from both data sources. If both data sources return `verified=true`, then `multiVerify=true`. If both data sources return `verified=false`, then `multiVerify=false`. If one data source returns `verified=true` and the other returns `verified=false`, then `multiVerify=true`. 

The Identity Verify response has also been updated to include a new parameter for the CIP confidence response (labeled `multiCIPConfidence`) that uses the rules below to calculate high or low for this parameter. The CIPConfidence response parameter within each data source Verify response will use the current CIPConfidence logic

**Strict**

At least 2 submitted parameters must match both data sources to receive a high result. Otherwise, the result is low.

**Normal**

At least 2 submitted parameters must match one of the data sources to receive a high result. Otherwise, the result is low.

> 📘 Splunk
> 
> `multiVerify` and `multiCIPConfidence` as well as the Verify information from the second source will be logged under STAT level logging in Splunk.
> 
> [block:image]
> {
>   "images": [
>     {
>       "image": [
>         "https://files.readme.io/9a700b7-unnamed_2.png",
>         null,
>         null
>       ],
>       "align": "center"
>     }
>   ]
> }
> [/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/6e97761-unnamed_1.png",
        null,
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/c545b7f-unnamed.png",
        null,
        ""
      ],
      "align": "center"
    }
  ]
}
[/block

```json
{
	"requestId":"KW-{{$timestamp}}",
	"phoneNumber":"19292937552", 
	"consentStatus":"optedIn", 
	"firstName":"Michelle", 
	"lastName":"Jones", 
	"address":"3118 S Broadway St",
	"city":"Denver", 
	"region":"CO",
	"postalCode":"80218",
	"dob":"1972-02-20",
	"lastVerified":"",
	"ssn":"555221113",
	"phoneUpdate":"true",
	"details":true
}

```

```json
{
    "requestId": "KW-1689611154",
    "status": 0,
    "description": "Success.",
    "response": {
        "transactionId": "165297914",
        "payfoneAlias": "5636847C4VKDEO11277417E68907236DD0MEK19P4SF9P32F603DFDC670B7AA17614C69901F610AAFF6G3B41390B35BF97535BFBBE43CAEF3C701676C",
        "phoneNumber": "19292937552",
        "lineType": "Mobile",
        "carrier": "T-Mobile USA",
        "countryCode": "US",
        "verified": true,
        "multiVerified": true,
        "multiCipConfidence": "low",
        "cipConfidence": "low",
        "name": {
            "firstName": 99,
            "lastName": 100,
            "nameScore": 99
        },
        "address": {
            "streetNumber": 21,
            "street": false,
            "city": false,
            "region": false,
            "postalCode": false,
            "distance": 846.84,
            "addressScore": 20
        },
        "identifiers": {
            "ssn": false,
            "dob": false
        },
        "reasonCodes": [
            "NN",
            "NO",
            "OL",
            "RM",
            "UV"
        ],
        "matchDataType": "nonCarrier",
        "dataSource2": {
            "name": {
                "firstName": 100,
                "lastName": 100,
                "nameScore": 100
            },
            "address": {
                "streetNumber": 40,
                "street": false,
                "city": true,
                "region": true,
                "postalCode": true,
                "distance": 0.0,
                "addressScore": 33
            },
            "identifiers": {
                "ssn": true,
                "dob": true
            },
            "reasonCodes": [
                "OD",
                "OL",
                "OO",
                "P5",
                "RM",
                "S1",
                "S2",
                "UV"
            ],
            "cipConfidence": "low",
            "verified": true
        }
    }
}

```

## Enhancements

The following describes enhancements that were added in this release. 

### Howlback - Updates

Additional updates were made to the Howlback Admin and Client tools. These tools are used as AT&T onboarding tools to help a client implement a new BOSE server.

### 1. AUTH-[1361](https://payfone.jira.com/browse/AUTH-1361): Mobile Auth - Synchrony Failing with a 410

URL decoding of the URL encoded `requires-consent` parameter was added.  Previously, AT&T was not URL encoding the parameter, and recently it seems they began to do so, which required additional decoding to ensure that we would be able to obtain the vfp in the URL properly.

It should also be noted that this problem is not widespread and only occurs occasionally on Synchrony calls.

### 2. TRST-[1034](https://payfone.jira.com/browse/TRST-1034): Implement Onboarding Model into Trust Score

A new trust score model was introduced that focuses on onboarding new customers. You can find more information about this model [here](https://payfone.jira.com/browse/PT-2000). This model was added to Payfex as shown below, referred to as **Onboarding Model**.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/feee340-image-20230711-215658.png",
        null,
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]