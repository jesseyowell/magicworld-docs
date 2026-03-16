---
title: Import Vouchers
excerpt: >-
  Import standalone vouchers and gift cards into the repository.


  <!-- theme: info -->


  > 📘 Important notes

  >

  > - **Start and expiration dates** need to be provided in compliance with the
  ISO 8601 norms. For example, 2020-03-11T09:00:00.000Z.

  > - Custom code attributes (not supported by-default) need to be added as code
  **metadata**.

  > - You **cannot import the same codes** to a single Voucherify Project.


  Any parameters not provided in the payload will be left blank or null.


  For both **standalone discount vouchers and gift cards**, you can import the
  following fields:  


  - code

  - category

  - active

  - type

  - start_date

  - expiration_date

  - redemption.quantity

  - additional_info

  - metadata


  For **gift cards**, you can also import the following field:


  - gift.amount


  For **discount vouchers**, you can import the `discount` object. The object
  will slightly vary depending on the type of discount. Each discount type
  **requires** the `type` to be defined in the import.


  | **Discount Type** | **Required fields** |

  |:---|:---|

  | Amount | amount_off, effect |

  | Percent | percent_off, effect |

  | Fixed | fixed_amount, effect |

  | Unit - One item | unit_off, unit_type, effect |

  | Unit - Multiple items | unit_off, unit_type, effect |

  | Shipping | unit_off, unit_type, effect |


  Fields other than the ones listed above won't be imported. Even if provided,
  they will be silently skipped.


  This API request starts a process that affects Voucherify data in bulk. 


  In case of small jobs (like bulk update) the request is put into a queue and
  processed once every other bulk request placed in the queue prior to this
  request is finished. However, when the job takes a longer time (like vouchers
  generation) then it is processed in small portions in a round-robin fashion.
  When there is a list of vouchers generation scheduled, then they will all have
  the `IN_PROGRESS` status shortly. This way, small jobs added just after
  scheduling big jobs of the same type will be processed in a short time
  window. 


  The result will return the async ID. You can verify the status of your request
  via this [API request](ref:get-async-action).
api:
  file: voucherify-api.json
  operationId: post-vouchers-import
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---