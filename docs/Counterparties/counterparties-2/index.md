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
<HTMLBlock>{`
<div>A <mark>counterparty</mark> is a Buyer or a Supplier in our system. This can be an individual or a business.</div>

<style></style>
`}</HTMLBlock>

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        Field
      </th>

      <th style={{ textAlign: "left" }}>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td style={{ textAlign: "left" }}>
        **id**
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Unique identifier for the counterparty.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **name**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Display name of the counterparty.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **type**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Type of  the counterparty: Buyer or Supplier.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **address\_1**\
        *string*
      </td>

      <td style={{ textAlign: "left" }}>
        Street address of the counterparty  - Address Line 1.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **address\_2**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Street address of the  counterparty  - Address Line 2.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **city**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        City of the counterparty.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **state**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        State of the counterparty.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **zipcode**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Zipcode of the counterparty.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **country**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Country of the counterparty.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **primary\_contact\_email**\
        *string*
      </td>

      <td style={{ textAlign: "left" }}>
        Email of primary contact person representing the counterparty.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **remit\_email**\
        *string*
      </td>

      <td style={{ textAlign: "left" }}>
        Email to be used for remit notifications.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **primary\_contact\_name**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Name of primary contact person.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **primary\_contact\_phone**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Phone of primary contact person.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **bank\_account\_number**\
        *string*
      </td>

      <td style={{ textAlign: "left" }}>
        Bank account number of counterparty.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **bank\_routing\_number**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Bank routing number of counterparty.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **payment\_method**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Preffered payment method for counterparty.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **internal\_id**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Optional internal identifier for this counterparty.\
        If provided, this value must be unique for counterparty type.
      </td>
    </tr>
  </tbody>
</Table>

```json Sample Counterparty
{
    "id": "Unique-id-of-counterparty",
   
    "name": "Finexio Inc.",
    
    "type": "Buyer",
    
    "created": "2019-02-26T20:13:46.925922",
    
    "updated": "2020-05-06T20:43:42.109670",
    
    "address_1": "Address Line 1 Here",
    
    "address_2": "Address Line 1 Here",
    
    "city": "City Name",
    
    "state": "State Code",
    
    "zipcode": "32751",
    
    "country": "USA",
    
    "primary_contact_email": "test@gmail.com",
    
    "remit_email": null,
    
    "primary_contact_name": "Full Name",
    
    "primary_contact_phone": "123-456-78",
    
    "bank_account_number": "1234",
    
    "bank_routing_number": "123456789",
    
    "payment_method": null,
    
    "internal_id": "FINEXIO-BUYER"
}
```
