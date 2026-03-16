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
# Webhooks - Example Payloads

## `product.update`

```json
{
    "active": true,
    "attributed_cost": null,
    "base_name": "Post Shave Balm",
    "brand": {
        "id": "0624dbcd-ef13-11e6-e986-fcc1c343cd6a",
        "name": "Harrys"
    },
    "button_order": 1,
    "categories": [],
    "deleted_at": null,
    "description": "",
    "handle": "postshavebalm",
    "id": "0624dbcd-ef13-11e6-e986-fcc1c366e772",
    "inventory": [{
        "attributed_cost": "10.00",
        "count": 2,
        "id": "0db6c587-0bcb-c168-561d-89aba2fab7c0",
        "outlet_id": "0624dbcd-ef95-11e6-e986-ecd5a64d7fa9",
        "product_id": "0624dbcd-ef13-11e6-e986-fcc1c366e772",
        "reorder_point": "0",
        "restock_level": "0"
    }, {
        "attributed_cost": "10.00",
        "count": 7,
        "id": "380e2ad4-3c38-5517-e110-9f927920a8cf",
        "outlet_id": "0624dbcd-ef13-11e6-e986-ed89c9e5529a",
        "product_id": "0624dbcd-ef13-11e6-e986-fcc1c366e772",
        "reorder_point": "0",
        "restock_level": "0"
    }, {
        "attributed_cost": "10.00",
        "count": 10,
        "id": "902c62e8-ce08-cfe6-e3b9-1a639a24a4c8",
        "outlet_id": "0624dbcd-ef13-11e6-e986-eda415b5a980",
        "product_id": "0624dbcd-ef13-11e6-e986-fcc1c366e772",
        "reorder_point": "0",
        "restock_level": "0"
    }],
    "name": "Post Shave Balm",
    "price_book_entries": [{
        "customer_group_id": "0624dbcd-ef95-11e6-e986-ecd5a641a9d9",
        "customer_group_name": "All Customers",
        "id": "62d5e8f2-884b-e3d0-29e0-8cadccf0aa91",
        "max_units": null,
        "min_units": null,
        "price": "6.95652",
        "product_id": "0624dbcd-ef13-11e6-e986-fcc1c366e772",
        "type": "BASE",
        "valid_from": null,
        "valid_to": null
    }],
    "product_type": {
        "id": "0624dbcd-ef13-11e7-e986-0b97f9762984",
        "name": "General"
    },
    "retailer_id": "0624dbcd-ef95-11e6-e986-ecd5a63e28e2",
    "sku": "10107",
    "source": "SHOPIFY",
    "source_id": "17238228994",
    "source_variant_id": "61863821314",
    "supplier": {
        "description": "",
        "id": "0624dbcd-ef13-11e6-e986-fcc061d142ab",
        "name": "Harrys",
        "source": ""
    },
    "supply_price": "4.00",
    "taxes": [{
        "outlet_id": "0624dbcd-ef13-11e6-e986-ed89c9e5529a",
        "tax_id": "0624dbcd-ef95-11e6-e986-ecd5a645338e"
    }, {
        "outlet_id": "0624dbcd-ef13-11e6-e986-eda415b5a980",
        "tax_id": "0624dbcd-ef95-11e6-e986-ecd5a645338e"
    }, {
        "outlet_id": "0624dbcd-ef95-11e6-e986-ecd5a64d7fa9",
        "tax_id": "0624dbcd-ef95-11e6-e986-ecd5a645338e"
    }],
    "variant_options": [],
    "variant_parent_id": null,
    "version": 5303657190
}
```

## inventory.update

```json
{
    "attributed_cost": "15.57",
    "count": 10,
    "id": "180e2ad4-1c18-5517-e110-9f927920a8cf",
    "outlet": {
        "id": "0924dbcd-ef11-11e9-e989-ed89c9e5529a",
        "name": "Shop 1",
        "tax_id": "0924dbcd-ef95-11e9-e989-ecd5a945118e",
        "time_zone": "Pacific/Auckland"
    },
    "outlet_id": "0924dbcd-ef11-11e9-e989-ed89c9e5529a",
    "product": {
        "active": true,
        "attributed_cost": null,
        "base_name": "Post Shave Balm",
        "button_order": 1,
        "categories": [],
        "deleted_at": null,
        "description": "",
        "handle": "postshavebalm",
        "id": "0924dbcd-ef11-11e9-e989-fcc1c199e772",
        "name": "Post Shave Balm",
        "sku": "10107",
        "source": "SHOPIFY",
        "source_id": "17218228994",
        "source_variant_id": "91891821114",
        "supply_price": "4.00",
        "taxes": [{
            "outlet_id": "0924dbcd-ef11-11e9-e989-ed89c9e5529a",
            "tax_id": "0924dbcd-ef95-11e9-e989-ecd5a945118e"
        }, {
            "outlet_id": "0924dbcd-ef11-11e9-e989-eda415b5a980",
            "tax_id": "0924dbcd-ef95-11e9-e989-ecd5a945118e"
        }, {
            "outlet_id": "0924dbcd-ef95-11e9-e989-ecd5a94d7fa9",
            "tax_id": "0924dbcd-ef95-11e9-e989-ecd5a945118e"
        }],
        "variant_options": [],
        "variant_parent_id": null
    },
    "product_id": "0924dbcd-ef11-11e9-e989-fcc1c199e772",
    "reorder_point": "0",
    "restock_level": "0",
    "version": 5105100802
}
```

## consignment.send

```json
{
    "id": "0afa8de1-1441-11e7-edec-da436c01fae6",
    "consignment_id": "0afa8de1-1441-11e7-edec-da43672aaf45",
    "product_id": "0624dbcd-ef13-11e6-e986-fcca33dee6e6",
    "count": "1.00000",
    "received": null,
    "cost": 0.3,
    "sequence_number": 2
}
```

## consignment.receive

```json
{
    "id": "0afa8de1-1441-11e7-edec-da42913731c8",
    "consignment_id": "0afa8de1-1441-11e7-edec-da427ee4bec7",
    "product_id": "0624dbcd-ef13-11e6-e986-fcc1c366e772",
    "count": "8.00000",
    "received": "8.00000",
    "cost": 4,
    "sequence_number": 5
}
```

## sale.update

```json
{
    "created_at": "2017-12-06 04:30:39",
    "customer": {
        "balance": "0.00000",
        "company_name": null,
        "contact_first_name": null,
        "contact_last_name": null,
        "created_at": "2017-02-07 01:35:04",
        "custom_field_1": null,
        "custom_field_2": null,
        "custom_field_3": null,
        "custom_field_4": null,
        "customer_code": "WALKIN",
        "customer_group_id": "0624dbcd-ef95-11e6-e986-ecd5a641a9d9",
        "date_of_birth": null,
        "deleted_at": null,
        "do_not_email": false,
        "email": null,
        "enable_loyalty": false,
        "fax": null,
        "first_name": null,
        "id": "0624dbcd-ef95-11e6-e986-ecd5a6420648",
        "last_name": null,
        "loyalty_balance": "0.00000",
        "mobile": null,
        "note": null,
        "phone": null,
        "points": 0,
        "sex": null,
        "updated_at": "2017-02-07 01:35:04",
        "year_to_date": "0.00000"
    },
    "customer_id": "0624dbcd-ef95-11e6-e986-ecd5a6420648",
    "deleted_at": null,
    "id": "edf73c5e-a3e1-bfe7-11e7-da38dadd8a59",
    "invoice_number": "402",
    "note": "",
    "register_id": "0624dbcd-ef13-11e6-e986-ed89e1aa6310",
    "register_sale_payments": [{
        "amount": 50,
        "id": "edf73c5e-a3e1-a062-11e7-da3e33f28341",
        "payment_date": "2017-12-06T04:30:35Z",
        "payment_type": {
            "has_native_support": false,
            "id": "1",
            "name": "Cash"
        },
        "payment_type_id": 1,
        "retailer_payment_type": {
            "config": null,
            "id": "0624dbcd-ef95-11e6-e986-ecd5a64f97d5",
            "name": "Cash",
            "payment_type_id": "1"
        },
        "retailer_payment_type_id": "0624dbcd-ef95-11e6-e986-ecd5a64f97d5"
    }, {
        "amount": 23,
        "id": "edf73c5e-a3e1-a062-11e7-da3e346baae2",
        "payment_date": "2017-12-06T04:30:36Z",
        "payment_type": {
            "has_native_support": false,
            "id": "3",
            "name": "Credit Card"
        },
        "payment_type_id": 3,
        "retailer_payment_type": {
            "config": null,
            "id": "0624dbcd-ef95-11e6-e986-ecd5a64fe78e",
            "name": "EFTPOS",
            "payment_type_id": "3"
        },
        "retailer_payment_type_id": "0624dbcd-ef95-11e6-e986-ecd5a64fe78e"
    }],
    "register_sale_products": [{
        "discount": "0.00000",
        "id": "edf73c5e-a3e1-a062-11e7-da3e31230f8b",
        "loyalty_value": "65.00000",
        "price": "56.52174",
        "price_set": false,
        "price_total": "56.52174",
        "product_id": "0624dbcd-ef13-11e6-e986-ee7c6d0f6301",
        "quantity": 1,
        "tax": "8.47826",
        "tax_id": "0624dbcd-ef95-11e6-e986-ecd5a645338e",
        "tax_total": "8.47826"
    }, {
        "discount": "0.00000",
        "id": "edf73c5e-a3e1-a062-11e7-da3e316548ae",
        "loyalty_value": "8.00000",
        "price": "6.95652",
        "price_set": false,
        "price_total": "6.95652",
        "product_id": "0624dbcd-ef13-11e6-e986-fcc1c366e772",
        "quantity": 1,
        "tax": "1.04348",
        "tax_id": "0624dbcd-ef95-11e6-e986-ecd5a645338e",
        "tax_total": "1.04348"
    }],
    "sale_date": "2017-12-06T04:30:36Z",
    "short_code": "9t8zff",
    "source": "USER",
    "source_id": null,
    "status": "CLOSED",
    "taxes": [{
        "id": "a64cab6b-ecd5-11e6-8986-0624dbcdef95",
        "name": "GST",
        "rate": "0.15000",
        "tax": 9.52174
    }],
    "totals": {
        "total_loyalty": "73.00000",
        "total_payment": "73.00000",
        "total_price": "63.47826",
        "total_tax": "9.52174",
        "total_to_pay": "0.00000"
    },
    "updated_at": "2017-12-06T04:30:39+00:00",
    "user": {
        "created_at": "2017-02-07 01:35:04",
        "display_name": "Sherlock Homes",
        "email": "email@email.com",
        "id": "0624dbcd-ef95-11e6-e986-ecd5a6503836",
        "name": "email@email.com",
        "target_daily": null,
        "target_monthly": null,
        "target_weekly": null,
        "updated_at": "2017-10-25 03:34:24"
    },
    "user_id": "0624dbcd-ef95-11e6-e986-ecd5a6503836",
    "version": 5307658013
}
```

## customer.update

```json
{
    "id": "0624dbcd-ef13-11e6-e986-ed86b4f36850",
    "retailer_id": "0624dbcd-ef95-11e6-e986-ecd5a63e28e2",
    "customer_code": "Customer-JYU2",
    "customer_group_id": "0624dbcd-ef13-11e6-e986-ecd6db557107",
    "first_name": "John",
    "last_name": "Watson",
    "company_name": "Sherlock",
    "do_not_email": false,
    "email": "",
    "phone": "021111111",
    "mobile": "021111111",
    "fax": "",
    "balance": "202.980",
    "loyalty_balance": "8.60337",
    "enable_loyalty": true,
    "points": 0,
    "note": "",
    "year_to_date": "404.07001",
    "sex": "M",
    "date_of_birth": "1992-08-17 00:00:00",
    "custom_field_1": "",
    "custom_field_2": "",
    "custom_field_3": "",
    "custom_field_4": "",
    "updated_at": "2017-12-06 04:53:17",
    "created_at": "2017-02-07 22:42:29",
    "deleted_at": null,
    "contact": {
        "first_name": "John",
        "last_name": "Watson",
        "company_name": "Sherlock",
        "phone": "021111111",
        "mobile": "021111111",
        "fax": "",
        "email": "",
        "twitter": "",
        "website": "",
        "physical_address1": "221B Baker Street",
        "physical_address2": "",
        "physical_suburb": "",
        "physical_city": "London",
        "physical_postcode": "NW1 6XE",
        "physical_state": "",
        "physical_country_id": "UK",
        "postal_address1": "",
        "postal_address2": "",
        "postal_suburb": "",
        "postal_city": "London",
        "postal_postcode": "NW1 6XE",
        "postal_state": "",
        "postal_country_id": "UK"
    },
    "contact_first_name": "John",
    "contact_last_name": "Watson"
}
```

## register\_closure.create

```json
{
    "id": "0afa8de1-1441-11e7-edec-d5765a2132a1",
    "open_count_sequence": "23",
    "register_open_time": "2017-11-30 02:29:55",
    "register_close_time": "2017-11-30 04:57:53",
    "totals": {
        "sales": "435.95700",
        "onaccount": "0",
        "laybys": "0",
        "tax": "55.95654",
        "discounts": "0",
        "payments": "565.96000",
        "regular_payments": "565.96000",
        "onaccount_payments": "0",
        "layby_payments": "0",
        "loyalty": "435.95700",
        "cost_of_goods_sold": "288.48069"
    },
    "taxes": {
        "0624dbcd-ef95-11e6-e986-ecd5a645338e": {
            "name": "GST",
            "total": "55.95654",
            "rate": "0.150000",
            "taxable": "373.04346"
        },
        "0624dbcd-ef95-11e6-e986-ecd5a644349b": {
            "name": "No Tax",
            "total": "0.00000",
            "rate": "0.000000",
            "taxable": "6.95700"
        }
    },
    "payments_summary": {
        "0624dbcd-ef95-11e6-e986-ecd5a64f97d5": {
            "payment_type_name": "Cash",
            "total": "401.00000",
            "discrepancy": "0.00000"
        },
        "0624dbcd-ef95-11e6-e986-ecd5a64f4341": {
            "payment_type_name": "Cash rounding",
            "total": 0,
            "discrepancy": "0.00000"
        },
        "0624dbcd-ef95-11e6-e986-ecd5a64fe78e": {
            "payment_type_name": "EFTPOS",
            "total": "142.00000",
            "discrepancy": "0.00000"
        },
        "0624dbcd-ef13-11e6-e986-ed835b5040cc": {
            "payment_type_name": "Gift Card",
            "total": 0,
            "discrepancy": "0.00000"
        },
        "0624dbcd-ef13-11e6-e986-ed819a5b8767": {
            "payment_type_name": "Loyalty",
            "total": 0,
            "discrepancy": "0.00000"
        },
        "0624dbcd-ef13-11e6-e986-edad61c84050": {
            "payment_type_name": "PayPal Here",
            "total": 0,
            "discrepancy": "0.00000"
        },
        "0afa8de1-1413-11e7-edec-ad519f7f52de": {
            "payment_type_name": "Shopify",
            "total": 0,
            "discrepancy": "0.00000"
        },
        "0afa8de1-1413-11e7-edec-515d12212813": {
            "payment_type_name": "Smartpay",
            "total": 0,
            "discrepancy": "0.00000"
        },
        "0624dbcd-ef13-11e6-e986-ecd5a8188888": {
            "payment_type_name": "Store Credit",
            "total": 0,
            "discrepancy": "0.00000"
        },
        "0624dbcd-ef13-11e6-e986-f88527d728cc": {
            "payment_type_name": "Xero",
            "total": 0,
            "discrepancy": "0.00000"
        }
    },
    "payment_counts": [{
        "start_total": "0.00",
        "payments_total": "401.00",
        "withdrawals_total": "0.00",
        "close_total": "401.00",
        "payment_type": {
            "id": "0624dbcd-ef95-11e6-e986-ecd5a64f97d5",
            "name": "Cash",
            "payment_type_id": "1",
            "config": null
        }
    }, {
        "start_total": "0.00",
        "payments_total": "0.00",
        "withdrawals_total": "0.00",
        "close_total": "0.00",
        "payment_type": {
            "id": "0624dbcd-ef95-11e6-e986-ecd5a64f4341",
            "name": "Cash rounding",
            "payment_type_id": "122",
            "config": null
        }
    }, {
        "start_total": "0.00",
        "payments_total": "142.00",
        "withdrawals_total": "0.00",
        "close_total": "142.00",
        "payment_type": {
            "id": "0624dbcd-ef95-11e6-e986-ecd5a64fe78e",
            "name": "EFTPOS",
            "payment_type_id": "3",
            "config": "{\"url\":\"\",\"print\":true}"
        }
    }, {
        "start_total": "0.00",
        "payments_total": "0.00",
        "withdrawals_total": "0.00",
        "close_total": "0.00",
        "payment_type": {
            "id": "0624dbcd-ef13-11e6-e986-ed835b5040cc",
            "name": "Gift Card",
            "payment_type_id": "118",
            "config": null
        }
    }, {
        "start_total": "0.00",
        "payments_total": "0.00",
        "withdrawals_total": "0.00",
        "close_total": "0.00",
        "payment_type": {
            "id": "0624dbcd-ef13-11e6-e986-ed819a5b8767",
            "name": "Loyalty",
            "payment_type_id": "106",
            "config": "{\"url\":\"\\\/pay\\\/0624dbcd-ef13-11e6-e986-ed819a5b8767\"}"
        }
    }, {
        "start_total": "0.00",
        "payments_total": "0.00",
        "withdrawals_total": "0.00",
        "close_total": "0.00",
        "payment_type": {
            "id": "0624dbcd-ef13-11e6-e986-edad61c84050",
            "name": "PayPal Here",
            "payment_type_id": "119",
            "config": "{\"url\":\"\\\/pay\\\/0624dbcd-ef13-11e6-e986-edad61c84050\"}"
        }
    }, {
        "start_total": "0.00",
        "payments_total": "0.00",
        "withdrawals_total": "0.00",
        "close_total": "0.00",
        "payment_type": {
            "id": "0afa8de1-1413-11e7-edec-ad519f7f52de",
            "name": "Shopify",
            "payment_type_id": "3",
            "config": null
        }
    }, {
        "start_total": "0.00",
        "payments_total": "0.00",
        "withdrawals_total": "0.00",
        "close_total": "0.00",
        "payment_type": {
            "id": "0afa8de1-1413-11e7-edec-515d12212813",
            "name": "Smartpay",
            "payment_type_id": "114",
            "config": "{\"url\":\"https:\\\/\\\/api.smart-connect.cloud\\\/vend\\\/VendTransaction\"}"
        }
    }, {
        "start_total": "0.00",
        "payments_total": "0.00",
        "withdrawals_total": "0.00",
        "close_total": "0.00",
        "payment_type": {
            "id": "0624dbcd-ef13-11e6-e986-ecd5a8188888",
            "name": "Store Credit",
            "payment_type_id": "121",
            "config": null
        }
    }, {
        "start_total": "0.00",
        "payments_total": "0.00",
        "withdrawals_total": "0.00",
        "close_total": "0.00",
        "payment_type": {
            "id": "0624dbcd-ef13-11e6-e986-f88527d728cc",
            "name": "Xero",
            "payment_type_id": "107",
            "config": null
        }
    }],
    "register": {
        "id": "0624dbcd-ef13-11e6-e986-ed89e1aa6310",
        "name": "Shop 1 Register",
        "outlet_id": "0624dbcd-ef13-11e6-e986-ed89c9e5529a",
        "outlet_name": "Shop 1"
    }
}
```
