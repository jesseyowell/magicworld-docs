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
[block:api-header]
{
  "title": "Payment Method"
}
[/block]
For each supplier, payment method is normally managed by Finexio on a per-supplier basis. While testing, you can specify the payment method by specifying one of several special cities for a Supplier counterparty record. 

**Special cities:**
* Check Town
* Card City
* Achville
* Santa Wire
[block:api-header]
{
  "title": "Payment Outcome"
}
[/block]
By default, sandbox payments will simulate a successful payment outcome. The simulated time it takes to travel through the payment states depends on payment method (see [Payment Timing](#payment-timing)). In order to simulate unsuccessful payments, adjust the set of invoices that produce a given payment such that the *least* significant digits of the final payment amount as follows:
[block:parameters]
{
  "data": {
    "h-0": "amount_cents",
    "h-1": "outcome",
    "0-0": "_ _ _ _ _ _ 9900",
    "0-1": "**Complete** - (default) payment completed normally.",
    "2-0": "_ _ _ _ _ _ 9902",
    "2-1": "**Failed: Payment Returned** - payment was not accepted or returned by recipient or recipient's bank.",
    "3-0": "_ _ _ _ _ _ 9903",
    "3-1": "**Failed: Payment Cancelled** - payment was cancelled by sender.",
    "4-0": "_ _ _ _ _ _ 9904",
    "4-1": "**Failed: Payment Expired** - payment was not settled within specified limit (varies by payment method)",
    "1-0": "_ _ _ _ _ _ 9901",
    "1-1": "**Failed: Funding Error** - funds to pay this payment have not been received."
  },
  "cols": 2,
  "rows": 5
}
[/block]

[block:api-header]
{
  "title": "Payment Timing"
}
[/block]
By default, the payments generated in the sandbox will progress through the "happy-path" at a typical pace for a given payment method:
[block:parameters]
{
  "data": {
    "h-0": "Method",
    "h-1": "initiation<sup>1</sup>",
    "h-2": "in-progress",
    "h-3": "total",
    "0-0": "Check",
    "1-0": "Card",
    "2-0": "ACH",
    "3-0": "Wire",
    "0-1": "0-30 minutes",
    "1-1": "0-30 minutes",
    "2-1": "0-30 minutes",
    "3-1": "0-30 minutes",
    "h-4": "Total",
    "0-2": "6-30 days",
    "1-2": "2-10 days",
    "2-2": "3-7 days",
    "3-2": "1-4 days",
    "0-3": "3-5 days",
    "1-3": "1-10 days",
    "2-3": "1 days",
    "3-3": "1 days"
  },
  "cols": 3,
  "rows": 4
}
[/block]
For testing purposes, you can adjust the above timings by (TBD).

<sup>1</sup> time from posting invoices to payment creation.