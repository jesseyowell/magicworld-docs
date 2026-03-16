---
title: Create Orders Export
excerpt: >-
  Creates a downloadable CSV file containing a list of orders.


  The parameters listed in the payload resembles headers in the CSV file. To
  include a parameter to the file, add it to the `parameters.fields` object in
  the request body.


  The available filters are all <!-- [order
  object](OpenAPI.json/components/schemas/10_obj_order_object) -->[order
  object](ref:get-order) attributes. Additionally, any metadata defined in the
  metadata schema can be exported.


  Passing an empty JSON will generate a file containing three default fields:
  `id`, `source_id`, and `status`.


  The fields array is an array of strings containing the data in the export.
  These fields define the headers in the CSV file. The array can be a
  combination of any of the following available fields:


  | **Field** | **Definition** | **Example Export** |

  |:---|:---|:---|

  | id | Unique order ID. | ord_A69RIxEdRsPuC6i8gFGVHUft |

  | source_id | Unique order source ID. | 8638 |

  | created_at | Timestamp in ISO 8601 format representing the date and time
  when the order was created. | 2022-03-09T09:16:32.521Z |

  | updated_at | Timestamp in ISO 8601 format representing the date and time
  when the order was last updated. | 2022-03-09T09:16:33.331Z |

  | status | Order status. | `PAID`, `CREATED`, `FULFILLED`, `CANCELED` |

  | amount | Total amount of order items. | 7700 |

  | discount_amount | Represents total amount of the discount applied to whole
  cart. | 500 |

  | items_discount_amount | Represents total amount of the discount applied to
  order line items. | 100 |

  | total_discount_amount | All discounts applied to the order including
  discounts applied to particular order line items and discounts applied to the
  whole cart. | 600 |

  | total_amount | Total order amount after applying all discounts. | 7100 |

  | customer_id | Customer unique ID. | cust_2G4fUQdCXUqp35nXNleav7bO |

  | referrer_id | Referrer unique ID. | cust_IkrTR674vvQvr9a4rDMiqglY |

  | metadata | Returns all order metadata. | Response will include all order
  metadata. |

  | metadata.X | Where X is the name of a particular order metadata property. |
  The returned value will depend on the type of data defined in the Dashboard >
  Project Settings > Metdata Schemas > Order. |
api:
  file: voucherify-api.json
  operationId: post-orders-export
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---