---
title: Webhooks
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
# Webhooks

Webhooks are one way that Vend can send automated messages or information to external systems. Webhooks can be described as ["user-defined callbacks made with HTTP"](https://en.wikipedia.org/wiki/Webhook). Once a webhook has been configured, every time an entity changes in Vend (for example, a sale or product record), Vend will forward HTTP messages to notify the configured destinations.

> *NOTE: Vend's webhooks are reliable, but we can't guarantee they'll be delivered. Because of this, polling APIs is the right way to keep systems in sync.*

# Adding a Webhook

* The primary way of creating webhooks for OAuth authorized apps is via the `/api/webhook` endpoint as described [here](/reference/0/spec/webhooks/createwebhook)

* Webhooks can also be added "manually" through the API setup page in the Vend backend. This page can be accessed by adding **/setup/api** at the end of the store's URL.

# Payload

When an event happens and triggers a webhook, we’ll send a **`POST`** request to the URL defined by the webhook. The **`POST`** request will be in the **UTF-8** charset, and `application/x-www-form-urlencoded` encoding.

The **`POST`** body will include a field named `payload`. This field contains a JSON-encoded object with details of the object that caused the hooked event. Other form fields (such as `environment` or `domain_prefix`) may be present but are not guaranteed to be.

The payload objects you’ll find in webhook requests are the same as those you’ll receive from **API 1.0**. So, for example, the product webhook should give you a product payload that’s the same as if you requested `/api/1.0/product/{id}`.

# Request timeout and retries

The server listening for webhooks has **_5 seconds_** to respond with a `2xx` response (usually `204` or `200`) to acknowledge successful delivery of the webhook. If there is no response within that time or the server responds with an error, the request will time out and it will be retried.
The request will be retried up to 20 times over 48h and those retries will be scheduled with exponential back-off.

# Verification

For added security, webhooks sent to OAuth-authorised applications are signed so they can be verified as originating from Vend and unaltered in transit. A hash-based message authentication code is used for the signature. If the webhook request contains a header as below, the application can verify the request.

```
X-Signature: signature=897hRT893qkA783M093ha903f,algorithm=HMAC-SHA256
```

To do this, generate a signature by hashing the webhook request body and compare it to the signature in the header for an exact match. Use the algorithm specified in the header and your application's `client_secret` as the hash key.

# Types

## **`product.update `**

The `product.update` webhook is fired when a product is updated. That means it should fire when the user, for example, changes a product description.

> **WARNING:** _This webhook is not the best choice for applications tracking inventory changes. There are a couple of reasons for this:
>- _NOT all events which cause an inventory change (e.g. sale, return, stock order/transfer) will trigger this webhook._
>- _inventory data included in the payload of this webhook may, in certain situations be not up to date with the latest state of the inventory._
>- _Applications looking for the most up to date data should be using the `inventory.update` webhook._

[Sample Payload](/tutorials/guides/webhooks/sample-payloads#productupdate)

## **`inventory.update`**

The `inventory.update` webhook is fired when a product’s inventory is updated. If a product does not use inventory tracking, this webhook won’t fire. This webhook is expected to fire when the product is sold or its quantity is adjusted directly or as a result of a consignment.

[Sample Payload](/tutorials/guides/webhooks/sample-payloads#inventoryupdate)

## **`consignment.send`**

The `consignment.send` webhook is fired when a product assigned to a consignment has been sent to its destination. Because of that, it will only be fired for **stock transfers** since this will cause a stock adjustment in the source outlet.

[Sample Payload](/tutorials/guides/webhooks/sample-payloads#consignmentsend)

## **`consignment.receive`**

The `consignment.receive` webhook is fired when a product assigned to a consignment has been received into stock affecting an inventory value by that of what is received. This event will fire on a supplier order, stock transfer or stocktake event.

[Sample Payload](/tutorials/guides/webhooks/sample-payloads#consignmentreceive)

## **`sale.update`**

The `sale.update` webhook is fired when a sale is updated (created or modified). For the majority of sales, this only happens once: when the customer buys products and makes payment. For special kinds of sale (layby, account sales), the update webhook usually happens more than once as when the sale is fully paid the sales status will be updated.

[Sample Payload](/tutorials/guides/webhooks/sample-payloads#saleupdate)

## **`customer.update`**

The `customer.update` webhook is fired whenever a customer is updated (created, deleted, modified). Making an account sale to a customer is expected to fire the webhook (because their account balance is updated), as is editing their name, address or other details.

[Sample Payload](/tutorials/guides/webhooks/sample-payloads#customerupdate)

## **`register_closure.create`**

The `register_closure.create` webhooks if fired every time the register is closed.

[Sample Payload](/tutorials/guides/webhooks/sample-payloads#register_closurecreate)