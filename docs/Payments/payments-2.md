---
title: Payments
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
<div>This section is a brief guide about <mark>payments</mark> management like 
  how to send or receive payment using one of the available payment methods: 
 PrintedCheck, ACH, Card and Wire
</div>

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
        Unique identifier for the payment.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **amount\_cents**\
        *integer* 
      </td>

      <td style={{ textAlign: "left" }}>
        Amount paid to be entered in cents
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **status**\
        *select*
      </td>

      <td style={{ textAlign: "left" }}>
        Current payment status:

        * \*pending\*\*: Payment is being prepared for payment.

        * \*in-progress\*\*: Payment for this invoice is in-progress.

        * \*complete\*\*: Payment for this invoice has been resolved.

        * \*failed\*\*: An exception has occurred during payment processing.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **payment\_method**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Method used for the payment. Available options are: PrintedCheck, ACH, Card and Wire
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **status\_detail**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Additional information regarding current status expressed as key-value pairs.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **invoices**\
        *object* 
      </td>

      <td style={{ textAlign: "left" }}>
        List of invoices associated with this payment.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **installments**\
        *object* 
      </td>

      <td style={{ textAlign: "left" }}>
        List of invoice installments associated with this payment.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **originating\_counterparty\_id**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        The ID of one of your organization's internal counterparties (Buyer) that will send payment.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **receiving\_counterparty\_id**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        The ID of one of your external counterparties (Supplier) that will receive payment.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **tracking\_id**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Its used to reference this payment when communicating with Finexio's Customer Support and Payment Operations teams.
      </td>
    </tr>
  </tbody>
</Table>
