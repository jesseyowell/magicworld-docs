---
title: Counterparties
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
[block:html]
{
  "html": "<div>A <mark>counterparty</mark> is a Buyer or a Supplier in our system. This can be an individual or a business.</div>\n\n<style></style>"
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "**id**\n*string* ",
    "0-1": "Unique identifier for the counterparty.",
    "1-0": "**name**\n*string* ",
    "2-0": "**type**\n*string* ",
    "3-0": "**address_1**\n*string*",
    "4-0": "**address_2** \n*string* ",
    "5-0": "**city** \n*string* ",
    "6-0": "**state** \n*string* ",
    "7-0": "**zipcode**\n*string* ",
    "8-0": "**country** \n*string* ",
    "9-0": "**primary_contact_email** \n*string*",
    "10-0": "**remit_email**\n*string*",
    "11-0": "**primary_contact_name**\n*string* ",
    "12-0": "**primary_contact_phone** \n*string* ",
    "13-0": "**bank_account_number**\n*string*",
    "14-0": "**bank_routing_number**\n*string* ",
    "15-0": "**payment_method**\n*string* ",
    "16-0": "**internal_id**\n*string* ",
    "1-1": "Display name of the counterparty.",
    "2-1": "Type of  the counterparty: Buyer or Supplier.",
    "3-1": "Street address of the counterparty  - Address Line 1.",
    "4-1": "Street address of the  counterparty  - Address Line 2.",
    "5-1": "City of the counterparty.",
    "6-1": "State of the counterparty.",
    "7-1": "Zipcode of the counterparty.",
    "8-1": "Country of the counterparty.",
    "9-1": "Email of primary contact person representing the counterparty.",
    "10-1": "Email to be used for remit notifications.",
    "11-1": "Name of primary contact person.",
    "12-1": "Phone of primary contact person.",
    "13-1": "Bank account number of counterparty.",
    "14-1": "Bank routing number of counterparty.",
    "15-1": "Preffered payment method for counterparty.",
    "16-1": "Optional internal identifier for this counterparty.\nIf provided, this value must be unique for counterparty type."
  },
  "cols": 2,
  "rows": 17
}
[/block]

[block:code]
{
  "codes": [
    {
      "code": "{\n    \"id\": \"Unique-id-of-counterparty\",\n   \n    \"name\": \"Finexio Inc.\",\n    \n    \"type\": \"Buyer\",\n    \n    \"created\": \"2019-02-26T20:13:46.925922\",\n    \n    \"updated\": \"2020-05-06T20:43:42.109670\",\n    \n    \"address_1\": \"Address Line 1 Here\",\n    \n    \"address_2\": \"Address Line 1 Here\",\n    \n    \"city\": \"City Name\",\n    \n    \"state\": \"State Code\",\n    \n    \"zipcode\": \"32751\",\n    \n    \"country\": \"USA\",\n    \n    \"primary_contact_email\": \"test@gmail.com\",\n    \n    \"remit_email\": null,\n    \n    \"primary_contact_name\": \"Full Name\",\n    \n    \"primary_contact_phone\": \"123-456-78\",\n    \n    \"bank_account_number\": \"1234\",\n    \n    \"bank_routing_number\": \"123456789\",\n    \n    \"payment_method\": null,\n    \n    \"internal_id\": \"FINEXIO-BUYER\"\n}",
      "language": "json",
      "name": "Sample Counterparty"
    }
  ],
  "sidebar": true
}
[/block]