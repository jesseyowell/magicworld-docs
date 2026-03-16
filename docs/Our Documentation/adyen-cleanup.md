---
title: adyen cleanup
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
**Gateway Website:**  https://www.adyen.com/
**Developer Documentation:** https://docs.adyen.com/api-explorer/Checkout/latest/overview
**Default Currency:** USD

[block:callout]
{
  "type": "info",
  "body": "3DS authentication values obtained from a previous authentication can be sent within the ThreeDSecure object via Payment Service's Card/Authorize and Card/Purchase endpoints. See example requests.",
  "title": "3DS Support"
}
[/block]
**Gateway Endpoints**
This implementation of Adyen forwards requests to the below endpoints, defaulting to v69. To use a different version, send that version in the *adyenApiVersion* parameter (detailed in parameter chart below). 
[block:callout]
{
  "type": "warning",
  "body": "Production requests must include the livePrefix field (detailed in parameters). TokenEx uses this field to forward requests to the appropriate endpoints. This field is not necessary for the Test environment.",
  "title": "Adyen Checkout Live Endpoints"
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Action",
    "h-1": "Prod Endpoint",
    "h-2": "Test Endpoint",
    "0-0": "Card Authorize, Card Purchase",
    "1-0": "Card Capture",
    "2-0": "Card Refund",
    "3-0": "Card Void",
    "0-1": "https://[random]-[company name]-checkout-live.adyenpayments.com/checkout/v69/payments",
    "0-2": "https://checkout-test.adyen.com/v69/payments",
    "1-2": "https://checkout-test.adyen.com/v69/payments/{paymentPspReference}/captures",
    "2-2": "https://checkout-test.adyen.com/v69/payments/{paymentPspReference}/refunds",
    "3-2": "https://checkout-test.adyen.com/v69/payments/{paymentPspReference}/cancels",
    "1-1": "https://[random]-[company name]-checkout-live.adyenpayments.com/checkout/v69/payments/{paymentPspReference}/captures",
    "2-1": "https://[random]-[company name]-checkout-live.adyenpayments.com/checkout/v69/payments/{paymentPspReference}/refunds",
    "3-1": "https://[random]-[company name]-checkout-live.adyenpayments.com/checkout/v69/payments/{paymentPspReference}/cancels"
  },
  "cols": 3,
  "rows": 4
}

[/block]
**Supported Parameters:**
<sup>* denotes a required field</sup>
[block:parameters]
{
  "data": {
    "h-0": "Field Name",
    "h-1": "Type",
    "h-2": "Adyen Mapping",
    "h-3": "Notes",
    "0-0": "gateway",
    "0-1": "string",
    "0-2": "N/A",
    "1-0": "testMode",
    "1-1": "boolean",
    "0-3": "AdyenDirect",
    "1-2": "N/A",
    "2-0": "username*",
    "2-1": "string",
    "2-2": "Username piece of Basic Auth",
    "3-0": "password*",
    "3-1": "string",
    "3-2": "Password piece of Basic Auth",
    "4-0": "privateKey*",
    "4-1": "string",
    "4-2": "x-api-key header",
    "5-0": "livePrefix",
    "5-1": "string",
    "5-2": "live endpoint prefix",
    "6-0": "adyenApiVersion",
    "6-1": "string",
    "7-0": "merchantId*",
    "7-1": "string",
    "7-2": "merchantAccount",
    "8-0": "orderInfo.orderId*",
    "8-1": "string",
    "8-2": "reference",
    "9-0": "orderInfo.customerId",
    "9-1": "string",
    "9-2": "additionalData.enhancedSchemeData.customerReference",
    "10-0": "amount",
    "10-1": "numeric",
    "11-0": "currencyCode",
    "11-1": "string",
    "10-2": "amount.value",
    "11-2": "amount.currency",
    "12-0": "tax.amount",
    "12-1": "numeric",
    "12-2": "additionalData.enhancedSchemeData.totalTaxAmount",
    "14-0": "creditCard.number",
    "14-1": "string",
    "14-2": "paymentMethod.number",
    "15-0": "creditCard.expMonth",
    "15-1": "numeric",
    "15-2": "paymentMethod.expiryMonth",
    "16-0": "creditCard.expYear",
    "16-1": "numeric",
    "16-2": "paymentMethod.expiryYear",
    "17-0": "creditCard.cvv",
    "17-1": "string",
    "17-2": "paymentMethod.cvc",
    "18-0": "creditCard.brand",
    "18-1": "string",
    "18-2": "paymentMethod.brand",
    "13-0": "creditCard.fullName",
    "13-1": "string",
    "13-2": "paymentMethod.holderName",
    "19-0": "billingAddress.address1",
    "20-0": "billingAddress.address2",
    "21-0": "billingAddress.city",
    "22-0": "billingAddress.state",
    "23-0": "billingAddress.zip",
    "24-0": "billingAddress.country",
    "25-0": "billingAddress.email",
    "26-0": "shippingAddress.address1",
    "27-0": "shippingAddress.address2",
    "28-0": "shippingAddress.city",
    "29-0": "shippingAddress.state",
    "30-0": "shippingAddress.zip",
    "19-1": "string",
    "19-2": "billingAddress.houseNumberOrName",
    "20-1": "string",
    "21-1": "string",
    "22-1": "string",
    "23-1": "string",
    "24-1": "string",
    "25-1": "string",
    "26-1": "string",
    "27-1": "string",
    "28-1": "string",
    "29-1": "string",
    "30-1": "string",
    "20-2": "billingAddress.street",
    "21-2": "billingAddress.city",
    "22-2": "billingAddress.stateOrProvince",
    "23-2": "billingAddress.postalCode",
    "24-2": "billingAddress.country",
    "25-2": "shopperEmail",
    "31-0": "shippingAddress.country",
    "31-1": "string",
    "26-2": "deliveryAddress.houseNumberOrName",
    "27-2": "deliveryAddress.street",
    "28-2": "deliveryAddress.city",
    "29-2": "deliveryAddress.stateOrProvince",
    "30-2": "deliveryAddress.postalCode\nadditionalData.enhancedSchemeData.destinationPostalCode",
    "31-2": "deliveryAddress.country",
    "32-0": "threeDSecure.cavv",
    "32-1": "string",
    "32-2": "mpiData.cavv",
    "33-0": "threeDSecure.authenticationResponse",
    "33-1": "string",
    "33-2": "mpiData.authenticationResponse",
    "34-0": "threeDSecure.directoryResponse",
    "34-1": "string",
    "34-2": "mpiData.directoryResponse",
    "35-0": "threeDSecure.eci",
    "35-1": "string",
    "35-2": "mpiData.eci",
    "36-0": "threeDSecure.DSTransId",
    "36-1": "string",
    "36-2": "mpiData.dsTransID",
    "37-0": "threeDSecure.threeDSecureVersion",
    "37-1": "string",
    "37-2": "mpiData.threeDSVersion",
    "38-0": "storedCredentials.initiator",
    "38-1": "string",
    "38-2": "N/A",
    "39-0": "storedCredentials.credentialStored",
    "39-1": "boolean",
    "39-2": "shopperInteraction",
    "40-0": "storedCredentials.previousNetworkTransactionId",
    "40-1": "string",
    "40-2": "additionalData.networkTxReference",
    "41-0": "storedCredentials.TransactionType",
    "41-1": "string",
    "41-2": "recurringProcessingModel",
    "42-0": "softDescriptors.merchantPhone",
    "42-1": "string",
    "42-2": "shopperStatement",
    "43-1": "string",
    "43-2": "shopperStatement",
    "44-2": "shopperStatement",
    "45-2": "shopperStatement",
    "44-1": "string",
    "45-1": "string",
    "43-0": "softDescriptors.merchantUrl",
    "44-0": "softDescriptors.merchantEmail",
    "45-0": "softDescriptors.merchantName",
    "46-0": "shopperStatement",
    "46-1": "string",
    "46-2": "shopperStatement",
    "2-3": "Your Adyen User Name<br><sup>Not required if \"PrivateKey\" is provided<sup>",
    "3-3": "Your Adyen Password<br><sup>Not required if \"PrivateKey\" is provided<sup>",
    "4-3": "x-api-key from Adyen Portal<br><sup>Not required if \"UserName\" & \"Password\" is provided<sup>",
    "5-3": "Use this field to pass the merchant-specific live endpoint prefix.  https://docs.adyen.com/development-resources/live-endpoints#checkout-endpoints **Required for Production**",
    "6-2": "Adyen Checkout API version",
    "6-3": "Defaults to version 69. To change version, send target version as two digits. Example, \"70\".",
    "7-3": "The merchant account identifier with which you want to process the transaction.",
    "8-3": "The reference to uniquely identify a payment. If you need to provide multiple references for a transaction, separate them with hyphens (\"-\"). Maximum length: 80 characters.",
    "9-3": "Customer code, if supplied by a customer. Required for Level 2 data.",
    "10-3": "The amount in minor units. For example, 2000 means USD 20.00. Max length: 12 characters. Required for Level 2 data.",
    "11-3": "The three-character ISO currency code. [Alpha-3 ISO currency code](https://www.iso.org/iso-4217-currency-codes.html)<br/><br/>Use the ISO 4217 three-letter alphabetic code for the currency.",
    "13-3": "The name of the cardholder, as printed on the card.",
    "12-3": "Total tax amount, in minor units. For example, 2000 means USD 20.00. Max length: 12 characters. Required for Level 2 data.",
    "14-3": "Card number or TokenEx Token - TokenEx will replace the Token with the Detokenized number",
    "15-3": "The customer’s credit card expiration month. Format: 2 digits, zero-padded for single digits. Example: 03 = March, 11 = November",
    "16-3": "The customer’s credit card expiration year. Format: 4 digits. For example: 2030",
    "17-3": "The card verification code.",
    "18-3": "The brand of the customer's credit card.",
    "19-3": "The number or name of the house.",
    "20-3": "The name of the street.",
    "21-3": "The name of the city.",
    "22-3": "State or province codes as defined in ISO 3166-2. For example, CA in the US or ON in Canada.",
    "23-3": "A maximum of five digits for an address in the US, or a maximum of ten characters for an address in all other countries.",
    "24-3": "Three-Character Country Code [ISO country code](https://www.iso.org/iso-3166-country-codes.html).<br><sup>if provided, We convert this value to two-character country code. <br>In case this value is not sent with the billing address, it is auto-filled as \"ZZ\" as suggested by Adyen. <sup>",
    "25-3": "The shopper's email address.",
    "26-3": "The number or name of the house.",
    "27-3": "The name of the street.",
    "28-3": "The name of the city.",
    "29-3": "State or province codes as defined in ISO 3166-2. For example, CA in the US or ON in Canada.",
    "30-3": "A maximum of five digits for an address in the US, or a maximum of ten characters for an address in all other countries.",
    "31-3": "Three-Character Country Code [ISO country code](https://www.iso.org/iso-3166-country-codes.html).<br><sup>if provided, We convert this value to two-character country code. <br>In case this value is not sent with the shipping address, it is auto-filled as \"ZZ\" as suggested by Adyen. <sup>",
    "32-3": "The cardholder authentication value",
    "33-3": "This is the `transStatus` from the challenge result. If the transaction was frictionless, omit this parameter.",
    "34-3": "This is the `transStatus` from the `ARes` or Authentication response.",
    "35-3": "The electronic commerce indicator from the Authentication response.",
    "36-3": "The unique transaction identifier assigned by the Directory Server (DS) from the Authentication or Challenge Results response.",
    "37-3": "The EMV 3DS version used to authenticate the cardholder. Example, \"2.1.0\" or \"2.2.0\".",
    "38-3": "unmapped",
    "39-3": "See usage in [The Basics - Stored Credentials](doc:payment-services-v2-the-basics#stored-credentials). True = \"ContAuth\", False = \"Ecommerce\".",
    "40-3": "See usage in [The Basics - Stored Credentials](doc:payment-services-v2-the-basics#stored-credentials). Value obtained from Adyen response field additionalData.networkTxReference. This response field must be turned on from the Adyen portal -> Developers -> Additional Data -> Acquirer Section -> select Network Transaction Reference. Save configuration.",
    "41-3": "Valid values:<br>\"recurring\" = \"CardOnFile\",<br>\"installment\" = \"Subscription\",<br>\"unscheduled\" = \"UnscheduledCardOnFile\".<br>any other string value will be forwarded.",
    "46-3": "What appears on the customer's statement. [Adyen Docs ](https://docs.adyen.com/account/transaction-description#dynamic-values)",
    "42-3": "See note below.",
    "43-3": "See note below.",
    "44-3": "See note below.",
    "45-3": "See note below.",
    "1-3": "Routes between Sandbox and Production endpoints. All requests sent to the TokenEx test environment are sent to the Authorize.Net sandbox. This field value is honored in the TokenEx production environment.\nTokenEx Test: always true.\nTokenEx Prod: defaults to false."
  },
  "cols": 4,
  "rows": 47
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "Adyen API's shopperStatement is a free-text field. If values are sent in the TokenEx SoftDescriptor fields, they will be concatenated and space separated in the forwarded request. Alternatively, use the shopperStatement passthrough.\n\nExample usage:\n\"softDescriptors\": {\n        \"merchantName\":\"Bob Smalls\",\n        \"merchantPhone\": \"(876) 613-1270 x38785\",\n        \"merchantEmail\":\"bob@smalls.com\",\n        \"merchantUrl\": \"http://merchant.com\"\n    }\nForwarded output: Bob Smalls (876) 613-1270 x38785 bob@smalls.com http://merchant.com\n\n The value Adyen receives from ShopperStatement is visible within the Adyen merchant portal's description of that transaction's Shopper Details.",
  "title": "Soft Descriptors - ShopperStatement Construction"
}
[/block]
**Example Payloads:**
[block:code]
{
  "codes": [
    {
      "code": "{\n  \"gateway\": \"AdyenDirect\",\n  \"testMode\": true,\n  \"merchantId\": \"<Your merchant account identifier>\",\n  \"username\": \"<Your Adyen Username>\",\n  \"password\": \"<Your Adyen Password>\",\n  \"currencyCode\": \"USD\",\n  \"amount\": 150,\n  \"creditCard\": {\n    \"brand\": \"MasterCard\",\n    \"number\": \"5555341244441115\",\n    \"expMonth\": 12,\n    \"expYear\": 2030,\n    \"fullName\": \"Fredrick Gulgowski\",\n    \"cvv\": \"737\"\n  },\n  \"billingAddress\": {\n    \"phone\": \"793-358-4413 x1584\",\n    \"email\": \"Fredrick_Gulgowski@yahoo.com\",\n    \"company\": \"Wolff, Durgan and Satterfield\",\n    \"address1\": \"Suite 676\",\n    \"address2\": \"175 Cassin Manors\",\n    \"city\": \"Felipeshire\",\n    \"state\": \"MT\",\n    \"zip\": \"37685\",\n    \"country\": \"USA\"\n  },\n  \"orderInfo\": {\n    \"orderId\": \"ae34a289-1505-4c75-9ab1-a02490d6fc37\"\n  },\n  \"threeDSecure\": {\n    \"authenticationResponse\": \"Y\",\n    \"directoryResponse\": \"C\",\n    \"threeDSecureVersion\": \"2.1.0\",\n    \"eci\": \"02\",\n    \"cavv\": \"3q2+78r+ur7erb7vyv66vv\\\\/\\\\/\\\\/\\\\/8=\",\n    \"dsTransId\": \"76d5b612-ac0f-45a3-8166-3d5f99faf568\"\n  },\n  \"softDescriptors\": {\n    \"merchantName\": \"Bob Smalls\",\n    \"merchantPhone\": \"(876) 613-1270 x38785\",\n    \"merchantEmail\": \"bob@smalls.com\",\n    \"merchantUrl\": \"http://merchant.com\"\n  },\n  \"storedCredentials\": {\n    \"credentialStored\": true,\n    \"transactionType\": \"installment\",\n    \"previousNetworkTransactionId\": \"HKF5ISPDV0922\"\n  }\n}",
      "language": "json",
      "name": "Card Authorize/Purchase"
    },
    {
      "code": "{\n  \"gateway\": \"AdyenDirect\",\n  \"testMode\": true,\n  \"merchantId\": \"<Your merchant account identifier>\",\n  \"username\": \"<Your Adyen Username>\",\n  \"password\": \"<Your Adyen Password>\",\n  \"currencyCode\": \"USD\",\n  \"tokenExTransactionCode\": \"V1c4TDQ3UzVKVjVYOE44Mg==\",\n  \"amount\": 150\n}",
      "language": "json",
      "name": "Card Capture/Refund"
    },
    {
      "code": "{\n  \"gateway\": \"AdyenDirect\",\n  \"testMode\": true,\n  \"merchantId\": \"<Your merchant account identifier>\",\n  \"username\": \"<Your Adyen Username>\",\n  \"password\": \"<Your Adyen Password>\",\n  \"tokenExTransactionCode\": \"V0dWRDQ0TkdWTUsyV044Mg==\"\n}",
      "language": "json",
      "name": "Card Void"
    }
  ]
}
[/block]

**Gateway Response Fields:**
[block:parameters]
{
  "data": {
    "h-0": "Field Name",
    "h-1": "Type",
    "h-2": "Adyen Mapping",
    "h-3": "Notes",
    "0-0": "Approved",
    "1-0": "ApprovalCode",
    "2-0": "ProviderTransactionCode",
    "3-0": "TokenExTransactionCode",
    "0-1": "boolean",
    "1-1": "string",
    "2-1": "string",
    "3-1": "string",
    "0-2": "ResultCode (Primary transactions)\nStatus (Secondary transactions)",
    "0-3": "True when the following conditions are met.\nPrimary Transactions: ResultCode is \"authorised\"\nSecondary Transactions: Status is \"received\".",
    "2-2": "pspReference",
    "3-2": "pspReference",
    "1-2": "additionalData.authCode",
    "3-3": "Base64 encoded Adyen Checkout's pspReference. Required for use on secondary transactions.",
    "2-3": "Adyen's 16-character reference associated with the transaction/request.",
    "1-3": "Authorisation code"
  },
  "cols": 4,
  "rows": 4
}
[/block]