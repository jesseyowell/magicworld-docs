---
title: Testo
fullscreen: false
hidden: true
metadata:
  title: ''
  description: ''
---
This document provides feature descriptions and technical information about Prove’s latest release. As you plan your implementation or upgrades of new API features, remember that Prove’s Support team is always here to help.

**Release Dates**\
**Staging:** Tuesday, July 25th, 2023, at 3 PM MST\
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
> <Image align="center" src="https://files.readme.io/9a700b7-unnamed_2.png" />

<Image align="center" src="https://files.readme.io/6e97761-unnamed_1.png" />
