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
**Gateway Website:**  [https://www.adyen.com/](https://www.adyen.com/)\
**Developer Documentation:** [https://docs.adyen.com/api-explorer/Checkout/latest/overview](https://docs.adyen.com/api-explorer/Checkout/latest/overview)\
**Default Currency:** USD

> 📘 3DS Support
>
> 3DS authentication values obtained from a previous authentication can be sent within the ThreeDSecure object via Payment Service's Card/Authorize and Card/Purchase endpoints. See example requests.

**Gateway Endpoints**\
This implementation of Adyen forwards requests to the below endpoints, defaulting to v69. To use a different version, send that version in the *adyenApiVersion* parameter (detailed in parameter chart below). 

> 🚧 Adyen Checkout Live Endpoints
>
> Production requests must include the livePrefix field (detailed in parameters). TokenEx uses this field to forward requests to the appropriate endpoints. This field is not necessary for the Test environment.


<Table align={["left","left","left"]}>
  <thead>
    <tr>
      <th>
        Action
      </th>

      <th>
        Prod Endpoint
      </th>

      <th>
        Test Endpoint
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Card Authorize, Card Purchase
      </td>

      <td>
        https\://[random]-[company name]-checkout-live.adyenpayments.com/checkout/v69/payments
      </td>

      <td>
        [https://checkout-test.adyen.com/v69/payments](https://checkout-test.adyen.com/v69/payments)
      </td>
    </tr>

    <tr>
      <td>
        Card Capture
      </td>

      <td>
        https\://[random]-[company name]-checkout-live.adyenpayments.com/checkout/v69/payments/\{paymentPspReference}/captures
      </td>

      <td>
        [https://checkout-test.adyen.com/v69/payments/\{paymentPspReference}/captures](https://checkout-test.adyen.com/v69/payments/\{paymentPspReference}/captures)
      </td>
    </tr>

    <tr>
      <td>
        Card Refund
      </td>

      <td>
        https\://[random]-[company name]-checkout-live.adyenpayments.com/checkout/v69/payments/\{paymentPspReference}/refunds
      </td>

      <td>
        [https://checkout-test.adyen.com/v69/payments/\{paymentPspReference}/refunds](https://checkout-test.adyen.com/v69/payments/\{paymentPspReference}/refunds)
      </td>
    </tr>

    <tr>
      <td>
        Card Void
      </td>

      <td>
        https\://[random]-[company name]-checkout-live.adyenpayments.com/checkout/v69/payments/\{paymentPspReference}/cancels
      </td>

      <td>
        [https://checkout-test.adyen.com/v69/payments/\{paymentPspReference}/cancels](https://checkout-test.adyen.com/v69/payments/\{paymentPspReference}/cancels)
      </td>
    </tr>
  </tbody>
</Table>

**Supported Parameters:**\ <sup>\* denotes a required field</sup>


<Table align={["left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Field Name
      </th>

      <th>
        Type
      </th>

      <th>
        Adyen Mapping
      </th>

      <th>
        Notes
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        gateway
      </td>

      <td>
        string
      </td>

      <td>
        N/A
      </td>

      <td>
        AdyenDirect
      </td>
    </tr>

    <tr>
      <td>
        testMode
      </td>

      <td>
        boolean
      </td>

      <td>
        N/A
      </td>

      <td>
        Routes between Sandbox and Production endpoints. All requests sent to the TokenEx test environment are sent to the Authorize.Net sandbox. This field value is honored in the TokenEx production environment.\
        TokenEx Test: always true.\
        TokenEx Prod: defaults to false.
      </td>
    </tr>

    <tr>
      <td>
        username\*
      </td>

      <td>
        string
      </td>

      <td>
        Username piece of Basic Auth
      </td>

      <td>
        Your Adyen User Name<br /><sup>Not required if "PrivateKey" is provided</sup>
      </td>
    </tr>

    <tr>
      <td>
        password\*
      </td>

      <td>
        string
      </td>

      <td>
        Password piece of Basic Auth
      </td>

      <td>
        Your Adyen Password<br /><sup>Not required if "PrivateKey" is provided</sup>
      </td>
    </tr>

    <tr>
      <td>
        privateKey\*
      </td>

      <td>
        string
      </td>

      <td>
        x-api-key header
      </td>

      <td>
        x-api-key from Adyen Portal<br /><sup>Not required if "UserName" & "Password" is provided</sup>
      </td>
    </tr>

    <tr>
      <td>
        livePrefix
      </td>

      <td>
        string
      </td>

      <td>
        live endpoint prefix
      </td>

      <td>
        Use this field to pass the merchant-specific live endpoint prefix.  [https://docs.adyen.com/development-resources/live-endpoints#checkout-endpoints](https://docs.adyen.com/development-resources/live-endpoints#checkout-endpoints) **Required for Production**
      </td>
    </tr>

    <tr>
      <td>
        adyenApiVersion
      </td>

      <td>
        string
      </td>

      <td>
        Adyen Checkout API version
      </td>

      <td>
        Defaults to version 69. To change version, send target version as two digits. Example, "70".
      </td>
    </tr>

    <tr>
      <td>
        merchantId\*
      </td>

      <td>
        string
      </td>

      <td>
        merchantAccount
      </td>

      <td>
        The merchant account identifier with which you want to process the transaction.
      </td>
    </tr>

    <tr>
      <td>
        orderInfo.orderId\*
      </td>

      <td>
        string
      </td>

      <td>
        reference
      </td>

      <td>
        The reference to uniquely identify a payment. If you need to provide multiple references for a transaction, separate them with hyphens ("-"). Maximum length: 80 characters.
      </td>
    </tr>

    <tr>
      <td>
        orderInfo.customerId
      </td>

      <td>
        string
      </td>

      <td>
        additionalData.enhancedSchemeData.customerReference
      </td>

      <td>
        Customer code, if supplied by a customer. Required for Level 2 data.
      </td>
    </tr>

    <tr>
      <td>
        amount
      </td>

      <td>
        numeric
      </td>

      <td>
        amount.value
      </td>

      <td>
        The amount in minor units. For example, 2000 means USD 20.00. Max length: 12 characters. Required for Level 2 data.
      </td>
    </tr>

    <tr>
      <td>
        currencyCode
      </td>

      <td>
        string
      </td>

      <td>
        amount.currency
      </td>

      <td>
        The three-character ISO currency code. [Alpha-3 ISO currency code](https://www.iso.org/iso-4217-currency-codes.html)<br/><br/>Use the ISO 4217 three-letter alphabetic code for the currency.
      </td>
    </tr>

    <tr>
      <td>
        tax.amount
      </td>

      <td>
        numeric
      </td>

      <td>
        additionalData.enhancedSchemeData.totalTaxAmount
      </td>

      <td>
        Total tax amount, in minor units. For example, 2000 means USD 20.00. Max length: 12 characters. Required for Level 2 data.
      </td>
    </tr>

    <tr>
      <td>
        creditCard.fullName
      </td>

      <td>
        string
      </td>

      <td>
        paymentMethod.holderName
      </td>

      <td>
        The name of the cardholder, as printed on the card.
      </td>
    </tr>

    <tr>
      <td>
        creditCard.number
      </td>

      <td>
        string
      </td>

      <td>
        paymentMethod.number
      </td>

      <td>
        Card number or TokenEx Token - TokenEx will replace the Token with the Detokenized number
      </td>
    </tr>

    <tr>
      <td>
        creditCard.expMonth
      </td>

      <td>
        numeric
      </td>

      <td>
        paymentMethod.expiryMonth
      </td>

      <td>
        The customer’s credit card expiration month. Format: 2 digits, zero-padded for single digits. Example: 03 = March, 11 = November
      </td>
    </tr>

    <tr>
      <td>
        creditCard.expYear
      </td>

      <td>
        numeric
      </td>

      <td>
        paymentMethod.expiryYear
      </td>

      <td>
        The customer’s credit card expiration year. Format: 4 digits. For example: 2030
      </td>
    </tr>

    <tr>
      <td>
        creditCard.cvv
      </td>

      <td>
        string
      </td>

      <td>
        paymentMethod.cvc
      </td>

      <td>
        The card verification code.
      </td>
    </tr>

    <tr>
      <td>
        creditCard.brand
      </td>

      <td>
        string
      </td>

      <td>
        paymentMethod.brand
      </td>

      <td>
        The brand of the customer's credit card.
      </td>
    </tr>

    <tr>
      <td>
        billingAddress.address1
      </td>

      <td>
        string
      </td>

      <td>
        billingAddress.houseNumberOrName
      </td>

      <td>
        The number or name of the house.
      </td>
    </tr>

    <tr>
      <td>
        billingAddress.address2
      </td>

      <td>
        string
      </td>

      <td>
        billingAddress.street
      </td>

      <td>
        The name of the street.
      </td>
    </tr>

    <tr>
      <td>
        billingAddress.city
      </td>

      <td>
        string
      </td>

      <td>
        billingAddress.city
      </td>

      <td>
        The name of the city.
      </td>
    </tr>

    <tr>
      <td>
        billingAddress.state
      </td>

      <td>
        string
      </td>

      <td>
        billingAddress.stateOrProvince
      </td>

      <td>
        State or province codes as defined in ISO 3166-2. For example, CA in the US or ON in Canada.
      </td>
    </tr>

    <tr>
      <td>
        billingAddress.zip
      </td>

      <td>
        string
      </td>

      <td>
        billingAddress.postalCode
      </td>

      <td>
        A maximum of five digits for an address in the US, or a maximum of ten characters for an address in all other countries.
      </td>
    </tr>

    <tr>
      <td>
        billingAddress.country
      </td>

      <td>
        string
      </td>

      <td>
        billingAddress.country
      </td>

      <td>
        Three-Character Country Code [ISO country code](https://www.iso.org/iso-3166-country-codes.html).<br /><sup>if provided, We convert this value to two-character country code. <br />In case this value is not sent with the billing address, it is auto-filled as "ZZ" as suggested by Adyen.</sup>
      </td>
    </tr>

    <tr>
      <td>
        billingAddress.email
      </td>

      <td>
        string
      </td>

      <td>
        shopperEmail
      </td>

      <td>
        The shopper's email address.
      </td>
    </tr>

    <tr>
      <td>
        shippingAddress.address1
      </td>

      <td>
        string
      </td>

      <td>
        deliveryAddress.houseNumberOrName
      </td>

      <td>
        The number or name of the house.
      </td>
    </tr>

    <tr>
      <td>
        shippingAddress.address2
      </td>

      <td>
        string
      </td>

      <td>
        deliveryAddress.street
      </td>

      <td>
        The name of the street.
      </td>
    </tr>

    <tr>
      <td>
        shippingAddress.city
      </td>

      <td>
        string
      </td>

      <td>
        deliveryAddress.city
      </td>

      <td>
        The name of the city.
      </td>
    </tr>

    <tr>
      <td>
        shippingAddress.state
      </td>

      <td>
        string
      </td>

      <td>
        deliveryAddress.stateOrProvince
      </td>

      <td>
        State or province codes as defined in ISO 3166-2. For example, CA in the US or ON in Canada.
      </td>
    </tr>

    <tr>
      <td>
        shippingAddress.zip
      </td>

      <td>
        string
      </td>

      <td>
        deliveryAddress.postalCode\
        additionalData.enhancedSchemeData.destinationPostalCode
      </td>

      <td>
        A maximum of five digits for an address in the US, or a maximum of ten characters for an address in all other countries.
      </td>
    </tr>

    <tr>
      <td>
        shippingAddress.country
      </td>

      <td>
        string
      </td>

      <td>
        deliveryAddress.country
      </td>

      <td>
        Three-Character Country Code [ISO country code](https://www.iso.org/iso-3166-country-codes.html).<br /><sup>if provided, We convert this value to two-character country code. <br />In case this value is not sent with the shipping address, it is auto-filled as "ZZ" as suggested by Adyen.</sup>
      </td>
    </tr>

    <tr>
      <td>
        threeDSecure.cavv
      </td>

      <td>
        string
      </td>

      <td>
        mpiData.cavv
      </td>

      <td>
        The cardholder authentication value
      </td>
    </tr>

    <tr>
      <td>
        threeDSecure.authenticationResponse
      </td>

      <td>
        string
      </td>

      <td>
        mpiData.authenticationResponse
      </td>

      <td>
        This is the `transStatus` from the challenge result. If the transaction was frictionless, omit this parameter.
      </td>
    </tr>

    <tr>
      <td>
        threeDSecure.directoryResponse
      </td>

      <td>
        string
      </td>

      <td>
        mpiData.directoryResponse
      </td>

      <td>
        This is the `transStatus` from the `ARes` or Authentication response.
      </td>
    </tr>

    <tr>
      <td>
        threeDSecure.eci
      </td>

      <td>
        string
      </td>

      <td>
        mpiData.eci
      </td>

      <td>
        The electronic commerce indicator from the Authentication response.
      </td>
    </tr>

    <tr>
      <td>
        threeDSecure.DSTransId
      </td>

      <td>
        string
      </td>

      <td>
        mpiData.dsTransID
      </td>

      <td>
        The unique transaction identifier assigned by the Directory Server (DS) from the Authentication or Challenge Results response.
      </td>
    </tr>

    <tr>
      <td>
        threeDSecure.threeDSecureVersion
      </td>

      <td>
        string
      </td>

      <td>
        mpiData.threeDSVersion
      </td>

      <td>
        The EMV 3DS version used to authenticate the cardholder. Example, "2.1.0" or "2.2.0".
      </td>
    </tr>

    <tr>
      <td>
        storedCredentials.initiator
      </td>

      <td>
        string
      </td>

      <td>
        N/A
      </td>

      <td>
        unmapped
      </td>
    </tr>

    <tr>
      <td>
        storedCredentials.credentialStored
      </td>

      <td>
        boolean
      </td>

      <td>
        shopperInteraction
      </td>

      <td>
        See usage in [The Basics - Stored Credentials](doc:payment-services-v2-the-basics#stored-credentials). True = "ContAuth", False = "Ecommerce".
      </td>
    </tr>

    <tr>
      <td>
        storedCredentials.previousNetworkTransactionId
      </td>

      <td>
        string
      </td>

      <td>
        additionalData.networkTxReference
      </td>

      <td>
        See usage in [The Basics - Stored Credentials](doc:payment-services-v2-the-basics#stored-credentials). Value obtained from Adyen response field additionalData.networkTxReference. This response field must be turned on from the Adyen portal -> Developers -> Additional Data -> Acquirer Section -> select Network Transaction Reference. Save configuration.
      </td>
    </tr>

    <tr>
      <td>
        storedCredentials.TransactionType
      </td>

      <td>
        string
      </td>

      <td>
        recurringProcessingModel
      </td>

      <td>
        Valid values:<br />"recurring" = "CardOnFile",<br />"installment" = "Subscription",<br />"unscheduled" = "UnscheduledCardOnFile".<br />any other string value will be forwarded.
      </td>
    </tr>

    <tr>
      <td>
        softDescriptors.merchantPhone
      </td>

      <td>
        string
      </td>

      <td>
        shopperStatement
      </td>

      <td>
        See note below.
      </td>
    </tr>

    <tr>
      <td>
        softDescriptors.merchantUrl
      </td>

      <td>
        string
      </td>

      <td>
        shopperStatement
      </td>

      <td>
        See note below.
      </td>
    </tr>

    <tr>
      <td>
        softDescriptors.merchantEmail
      </td>

      <td>
        string
      </td>

      <td>
        shopperStatement
      </td>

      <td>
        See note below.
      </td>
    </tr>

    <tr>
      <td>
        softDescriptors.merchantName
      </td>

      <td>
        string
      </td>

      <td>
        shopperStatement
      </td>

      <td>
        See note below.
      </td>
    </tr>

    <tr>
      <td>
        shopperStatement
      </td>

      <td>
        string
      </td>

      <td>
        shopperStatement
      </td>

      <td>
        What appears on the customer's statement. [Adyen Docs ](https://docs.adyen.com/account/transaction-description#dynamic-values)
      </td>
    </tr>
  </tbody>
</Table>
> 📘 Soft Descriptors - ShopperStatement Construction
>
> Adyen API's shopperStatement is a free-text field. If values are sent in the TokenEx SoftDescriptor fields, they will be concatenated and space separated in the forwarded request. Alternatively, use the shopperStatement passthrough.
>
> Example usage:\
> "softDescriptors": \{\
>         "merchantName":"Bob Smalls",\
>         "merchantPhone": "(876) 613-1270 x38785",\
>         "merchantEmail":"[bob@smalls.com](mailto:bob@smalls.com)",\
>         "merchantUrl": "[http://merchant.com"](http://merchant.com")\
>     }\
> Forwarded output: Bob Smalls (876) 613-1270 x38785 [bob@smalls.com](mailto:bob@smalls.com) [http://merchant.com](http://merchant.com)
>
>  The value Adyen receives from ShopperStatement is visible within the Adyen merchant portal's description of that transaction's Shopper Details.

**Example Payloads:**


```json Card Authorize/Purchase
{
  "gateway": "AdyenDirect",
  "testMode": true,
  "merchantId": "<Your merchant account identifier>",
  "username": "<Your Adyen Username>",
  "password": "<Your Adyen Password>",
  "currencyCode": "USD",
  "amount": 150,
  "creditCard": {
    "brand": "MasterCard",
    "number": "5555341244441115",
    "expMonth": 12,
    "expYear": 2030,
    "fullName": "Fredrick Gulgowski",
    "cvv": "737"
  },
  "billingAddress": {
    "phone": "793-358-4413 x1584",
    "email": "Fredrick_Gulgowski@yahoo.com",
    "company": "Wolff, Durgan and Satterfield",
    "address1": "Suite 676",
    "address2": "175 Cassin Manors",
    "city": "Felipeshire",
    "state": "MT",
    "zip": "37685",
    "country": "USA"
  },
  "orderInfo": {
    "orderId": "ae34a289-1505-4c75-9ab1-a02490d6fc37"
  },
  "threeDSecure": {
    "authenticationResponse": "Y",
    "directoryResponse": "C",
    "threeDSecureVersion": "2.1.0",
    "eci": "02",
    "cavv": "3q2+78r+ur7erb7vyv66vv\\/\\/\\/\\/8=",
    "dsTransId": "76d5b612-ac0f-45a3-8166-3d5f99faf568"
  },
  "softDescriptors": {
    "merchantName": "Bob Smalls",
    "merchantPhone": "(876) 613-1270 x38785",
    "merchantEmail": "bob@smalls.com",
    "merchantUrl": "http://merchant.com"
  },
  "storedCredentials": {
    "credentialStored": true,
    "transactionType": "installment",
    "previousNetworkTransactionId": "HKF5ISPDV0922"
  }
}
```
```json Card Capture/Refund
{
  "gateway": "AdyenDirect",
  "testMode": true,
  "merchantId": "<Your merchant account identifier>",
  "username": "<Your Adyen Username>",
  "password": "<Your Adyen Password>",
  "currencyCode": "USD",
  "tokenExTransactionCode": "V1c4TDQ3UzVKVjVYOE44Mg==",
  "amount": 150
}
```
```json Card Void
{
  "gateway": "AdyenDirect",
  "testMode": true,
  "merchantId": "<Your merchant account identifier>",
  "username": "<Your Adyen Username>",
  "password": "<Your Adyen Password>",
  "tokenExTransactionCode": "V0dWRDQ0TkdWTUsyV044Mg=="
}
```

**Gateway Response Fields:**


<Table align={["left","left","left","left"]}>
  <thead>
    <tr>
      <th>
        Field Name
      </th>

      <th>
        Type
      </th>

      <th>
        Adyen Mapping
      </th>

      <th>
        Notes
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Approved
      </td>

      <td>
        boolean
      </td>

      <td>
        ResultCode (Primary transactions)\
        Status (Secondary transactions)
      </td>

      <td>
        True when the following conditions are met.\
        Primary Transactions: ResultCode is "authorised"\
        Secondary Transactions: Status is "received".
      </td>
    </tr>

    <tr>
      <td>
        ApprovalCode
      </td>

      <td>
        string
      </td>

      <td>
        additionalData.authCode
      </td>

      <td>
        Authorisation code
      </td>
    </tr>

    <tr>
      <td>
        ProviderTransactionCode
      </td>

      <td>
        string
      </td>

      <td>
        pspReference
      </td>

      <td>
        Adyen's 16-character reference associated with the transaction/request.
      </td>
    </tr>

    <tr>
      <td>
        TokenExTransactionCode
      </td>

      <td>
        string
      </td>

      <td>
        pspReference
      </td>

      <td>
        Base64 encoded Adyen Checkout's pspReference. Required for use on secondary transactions.
      </td>
    </tr>
  </tbody>
</Table>