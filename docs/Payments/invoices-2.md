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
[block:html]
{
  "html": "<div>Here you will see how <mark>invocies</mark> can be generated, listed and displayed</div>\n\n<style></style>"
}
[/block]

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Description",
    "0-0": "**id** \n*string* ",
    "1-0": "**amount_cents** \n*integer* ",
    "2-0": "**currency** \n*string* ",
    "3-0": "**discount_amount_cents**\n*integer* ",
    "4-0": "**invoice_date**\n*date* ",
    "5-0": "**invoice_due_date**\n*date* ",
    "6-0": "**line_items**\n*object* ",
    "7-0": "**note**\n*string* ",
    "8-0": "**originating_counterparty_id**\n*string* ",
    "9-0": "**receiving_counterparty_id**\n*string* ",
    "10-0": "**metadata**\n*object* ",
    "11-0": "**status**\n*select* ",
    "12-0": "**status_detail**\n*object*\n",
    "13-0": "**installments**\n*object*",
    "14-0": "**payment_id**\n*string* ",
    "0-1": "Unique identifier for the invoice.",
    "1-1": "Invoice amount in specified currency's smallest unit. e.g. $10 would be represented as 1000. min_value=1",
    "2-1": "Currency to be used for invoice payment",
    "3-1": "Optional invoice discount amount in specified currency's smallest unit.",
    "4-1": "Date of invoice provided by recipient. Must be +/- 365 days from today.",
    "5-1": "Optional invoice due date",
    "6-1": "Optional list of invoice line items to include in remittance data.",
    "7-1": "Optional additional information you would like to include regarding this invoice.",
    "8-1": "The ID of one of your organization's internal counterparties (Buyer) that will send payment.",
    "9-1": "The ID of one of your external counterparty (Supplier) that will receive invoice payment.",
    "10-1": "Additional private data represented as key-value pairs. Both the key and value must be strings or integers.",
    "11-1": "Status of current invoice. Following are available options:\n\n - pending: Invoice is being prepared for payment.\n - in-progress: Payment for this invoice is in-progress.\n - complete: Payment for this invoice has been resolved.\n - failed: An exception has occurred during payment processing.",
    "12-1": "Additional information regarding current status expressed as key-value pairs.",
    "13-1": "List of payment installments for this invoice. Typically, each invoice has just one installment for the full-amount.",
    "14-1": "The id of the most recent Payment associated with this invoice."
  },
  "cols": 2,
  "rows": 15
}
[/block]