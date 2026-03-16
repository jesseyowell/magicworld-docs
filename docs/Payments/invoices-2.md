---
title: Invoices
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
<div>Here you will see how <mark>invocies</mark> can be generated, listed and displayed</div>

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
        Unique identifier for the invoice.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **amount\_cents**\
        *integer* 
      </td>

      <td style={{ textAlign: "left" }}>
        Invoice amount in specified currency's smallest unit. e.g. $10 would be represented as 1000. min\_value=1
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **currency**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Currency to be used for invoice payment
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **discount\_amount\_cents**\
        *integer* 
      </td>

      <td style={{ textAlign: "left" }}>
        Optional invoice discount amount in specified currency's smallest unit.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **invoice\_date**\
        *date* 
      </td>

      <td style={{ textAlign: "left" }}>
        Date of invoice provided by recipient. Must be +/- 365 days from today.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **invoice\_due\_date**\
        *date* 
      </td>

      <td style={{ textAlign: "left" }}>
        Optional invoice due date
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **line\_items**\
        *object* 
      </td>

      <td style={{ textAlign: "left" }}>
        Optional list of invoice line items to include in remittance data.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **note**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        Optional additional information you would like to include regarding this invoice.
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
        The ID of one of your external counterparty (Supplier) that will receive invoice payment.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **metadata**\
        *object* 
      </td>

      <td style={{ textAlign: "left" }}>
        Additional private data represented as key-value pairs. Both the key and value must be strings or integers.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **status**\
        *select* 
      </td>

      <td style={{ textAlign: "left" }}>
        Status of current invoice. Following are available options:

        * pending: Invoice is being prepared for payment.
        * in-progress: Payment for this invoice is in-progress.
        * complete: Payment for this invoice has been resolved.
        * failed: An exception has occurred during payment processing.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **status\_detail**\
        *object*
      </td>

      <td style={{ textAlign: "left" }}>
        Additional information regarding current status expressed as key-value pairs.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **installments**\
        *object*
      </td>

      <td style={{ textAlign: "left" }}>
        List of payment installments for this invoice. Typically, each invoice has just one installment for the full-amount.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        **payment\_id**\
        *string* 
      </td>

      <td style={{ textAlign: "left" }}>
        The id of the most recent Payment associated with this invoice.
      </td>
    </tr>
  </tbody>
</Table>
