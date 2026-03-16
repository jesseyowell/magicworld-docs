---
title: Simulating Payments
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
When working in the sandbox (stage) environment, the system does not send real payments for uploaded invoices. This section details how to simulate various payment scenarios for testing purposes.

## Payment Method

For each supplier, payment method is normally managed by Finexio on a per-supplier basis. While testing, you can specify the payment method by specifying one of several special cities for a Supplier counterparty record. 

**Special cities:**

* Check Town
* Card City
* Achville
* Santa Wire

## Payment Outcome

By default, sandbox payments will simulate a successful payment outcome. The simulated time it takes to travel through the payment states depends on payment method (see [Payment Timing](#payment-timing)). In order to simulate unsuccessful payments, adjust the set of invoices that produce a given payment such that the *least* significant digits of the final payment amount as follows:

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        amount_cents
      </th>

      <th>
        outcome
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        * \_ \_ \_ \_ \_ 9900
      </td>

      <td>
        * \*Complete\*\* - (default) payment completed normally.
      </td>
    </tr>

    <tr>
      <td>
        * \_ \_ \_ \_ \_ 9901
      </td>

      <td>
        * \*Failed: Funding Error\*\* - funds to pay this payment have not been received.
      </td>
    </tr>

    <tr>
      <td>
        * \_ \_ \_ \_ \_ 9902
      </td>

      <td>
        * \*Failed: Payment Returned\*\* - payment was not accepted or returned by recipient or recipient's bank.
      </td>
    </tr>

    <tr>
      <td>
        * \_ \_ \_ \_ \_ 9903
      </td>

      <td>
        * \*Failed: Payment Cancelled\*\* - payment was cancelled by sender.
      </td>
    </tr>

    <tr>
      <td>
        * \_ \_ \_ \_ \_ 9904
      </td>

      <td>
        * \*Failed: Payment Expired\*\* - payment was not settled within specified limit (varies by payment method)
      </td>
    </tr>
  </tbody>
</Table>

## Payment Timing

By default, the payments generated in the sandbox will progress through the "happy-path" at a typical pace for a given payment method:

<Table align={["left","left","left"]}>
  <thead>
    <tr>
      <th>
        Method
      </th>

      <th>
        initiation

        <sup>

        1

        </sup>
      </th>

      <th>
        in-progress
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        Check
      </td>

      <td>
        0-30 minutes
      </td>

      <td>
        6-30 days
      </td>
    </tr>

    <tr>
      <td>
        Card
      </td>

      <td>
        0-30 minutes
      </td>

      <td>
        2-10 days
      </td>
    </tr>

    <tr>
      <td>
        ACH
      </td>

      <td>
        0-30 minutes
      </td>

      <td>
        3-7 days
      </td>
    </tr>

    <tr>
      <td>
        Wire
      </td>

      <td>
        0-30 minutes
      </td>

      <td>
        1-4 days
      </td>
    </tr>
  </tbody>
</Table>

For testing purposes, you can adjust the above timings by (TBD).

<sup>1</sup> time from posting invoices to payment creation.
