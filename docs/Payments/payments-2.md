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
[block:html]
{
  "html": "<div>This section is a brief guide about <mark>payments</mark> management like \n  how to send or receive payment using one of the available payment methods: \n PrintedCheck, ACH, Card and Wire\n</div>\n\n<style></style>"
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "**id**\n*string* ",
    "1-0": "**amount_cents**\n*integer* ",
    "2-0": "**status**\n*select*",
    "3-0": "**payment_method**\n*string* ",
    "4-0": "**status_detail**\n*string* ",
    "5-0": "**invoices**\n*object* ",
    "6-0": "**installments**\n*object* ",
    "7-0": "**originating_counterparty_id**\n*string* ",
    "8-0": "**receiving_counterparty_id**\n*string* ",
    "9-0": "**tracking_id**\n*string* ",
    "2-1": "Current payment status:\n\n**pending**: Payment is being prepared for payment.\n\n**in-progress**: Payment for this invoice is in-progress.\n\n**complete**: Payment for this invoice has been resolved.\n\n**failed**: An exception has occurred during payment processing.",
    "0-1": "Unique identifier for the payment.",
    "1-1": "Amount paid to be entered in cents",
    "3-1": "Method used for the payment. Available options are: PrintedCheck, ACH, Card and Wire",
    "5-1": "List of invoices associated with this payment.",
    "6-1": "List of invoice installments associated with this payment.",
    "4-1": "Additional information regarding current status expressed as key-value pairs.",
    "7-1": "The ID of one of your organization's internal counterparties (Buyer) that will send payment.",
    "8-1": "The ID of one of your external counterparties (Supplier) that will receive payment.",
    "9-1": "Its used to reference this payment when communicating with Finexio's Customer Support and Payment Operations teams."
  },
  "cols": 2,
  "rows": 10
}
[/block]