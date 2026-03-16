---
title: Get Async Action
excerpt: >-
  Check the result of a scheduled asynchronous operation.  


  The table below lists the possible types of async actions. The types are
  different for each endpoint generating the async action. If you would like to
  learn more about importing data into Voucherify, read more
  [here](https://support.voucherify.io/article/574-data-import).


  | **Types by Context** | **Endpoint** |

  |:---|:---|

  | **CAMPAIGN** |  |

  | CAMPAIGN.VOUCHERS_IMPORT | **POST**   <!--
  [/campaigns/{campaignId}/import](OpenAPI.json/paths/~1campaigns~1{campaignId}~1import/post)
  -->[/campaigns/{campaignId}/import](ref:import-vouchers-to-campaign) |

  | CAMPAIGN.VOUCHERS_IMPORT_CSV | **POST**   <!--
  [/campaigns/{campaignId}/importCSV](OpenAPI.json/paths/~1campaigns~1{campaignId}~1importCSV/post)
  -->[/campaigns/{campaignId}/importCSV](ref:import-vouchers-to-campaign-using-csv)
  |

  | CAMPAIGN.VOUCHERS_UPDATE | **PUT**
  [/campaigns/{campaignId}](ref:update-campaign) |

  | CAMPAIGN.VOUCHERS_DELETE | **DELETE** <!--
  [/campaigns/{campaignId}](OpenAPI.json/paths/~1campaigns~1{campaignId}/delete})
  -->[/campaigns/{campaignId}](ref:delete-campaign) |

  | CAMPAIGN.VOUCHERS_GENERATE | <ul><li>**POST** <!--
  [/campaigns](OpenAPI.json/paths/~1campaigns/post)
  -->[/campaigns](ref:create-campaign): asynchronous for campaigns with more
  than 1 voucher, synchronous for campaign with 1 voucher</li><li>**POST**   
  <!--
  [/campaigns/{campaignId}/vouchers](OpenAPI.json/paths/~1campaigns~1{campaignId}~1vouchers/post)
  -->[/campaigns/{campaignId}/vouchers](ref:add-vouchers-to-campaign)</li><ul> |

  | **CUSTOMERS** |  |

  | CUSTOMERS.IMPORT_CSV | **POST** <!--
  [/customers/importCSV](OpenAPI.json/paths/~1customers~1importCSV/post)
  -->[/customers/importCSV](ref:import-customers-using-csv) |

  | CUSTOMERS.BULK_UPDATE | **POST** <!--
  [/customers/bulk/async](OpenAPI.json/paths/~1customers~1bulk~1async/post)
  -->[/customers/bulk/async](ref:update-customers-in-bulk) |

  | CUSTOMERS.METADATA_UPDATE | **POST** <!--
  [/customers/metadata/async](OpenAPI.json/paths/~1customers~1metadata~1async/post)
  -->[/customers/metadata/async](ref:update-customers-metadata-in-bulk) |

  | **PRODUCTS** |  |

  | PRODUCTS.BULK_UPDATE | **POST** <!--
  [/products/bulk/async](OpenAPI.json/paths/~1products~1bulk~1async/post)
  -->[/products/bulk/async](ref:update-products-in-bulk)<br> |

  | PRODUCTS.METADATA_UPDATE | **POST** <!--
  [/products/metadata/async](OpenAPI.json/paths/~1products~1metadata~1async/post)
  -->[/products/metadata/async](ref:update-products-metadata-in-bulk) |

  | PRODUCTS.IMPORT_CSV | **POST** <!--
  [/products/importCSV](OpenAPI.json/paths/~1products~1importCSV/post)
  -->[/products/importCSV](ref:import-products-using-csv) |

  | SKUS.IMPORT_CSV | **POST** <!--
  [/skus/importCSV](OpenAPI.json/paths/~1skus~1importCSV/post)
  -->[/skus/importCSV](ref:import-skus-using-csv) |

  | **VOUCHERS** |  |

  | VOUCHERS.IMPORT | **POST** <!--
  [/vouchers/import](OpenAPI.json/paths/~1vouchers~1import/post)
  -->[/vouchers/import](ref:import-vouchers) |

  | VOUCHERS.IMPORT_CSV | **POST** <!--
  [/vouchers/importCSV](OpenAPI.json/paths/~1vouchers~1importCSV/post)
  -->[/vouchers/importCSV](ref:import-vouchers-using-csv) |

  | VOUCHERS.BULK_UPDATE | **POST** <!--
  [/vouchers/bulk/async](OpenAPI.json/paths/~1vouchers~1bulk~1async/post)
  -->[/vouchers/bulk/async](ref:update-vouchers-in-bulk)<br> |

  | VOUCHERS.METADATA_UPDATE | **POST** <!--
  [/vouchers/metadata/async](OpenAPI.json/paths/~1vouchers~1metadata~1async/post)
  -->[/vouchers/metadata/async](ref:update-vouchers-metadata-in-bulk) | 

  | **ORDERS** |  |

  | ORDERS.IMPORT | **POST** [/orders/import](ref:import-orders) |

  | **METADATA KEY PURGE** |  |

  |
  CAMPAIGNS.METADATA_KEY_PURGE<br>CUSTOMERS.METADATA_KEY_PURGE<br>PRODUCTS.METADATA_KEY_PURGE<br>VOUCHERS.METADATA_KEY_PURGE<br>ORDERS.METADATA_KEY_PURGE
  | No API endpoint equivalent. You can perform this action through the
  Dashboard. See Dashboard documentation: Dashboard > [Project
  Settings](https://support.voucherify.io/article/99-schema-validation-metadata#maintenance)
  |
api:
  file: voucherify-api.json
  operationId: get-async-actions-async_action_id
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---