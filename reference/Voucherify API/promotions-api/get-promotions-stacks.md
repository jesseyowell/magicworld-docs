---
title: List Promotion Stacks
excerpt: >-
  This method enables you to list promotion stacks irrespective of the campaign
  they are associated with. 


  You can use filters in the query parameters to specify the stacks to be
  returned in the response.


  ## Advanced filters for fetching promotion stacks


  | **Filters** | **Examples** |

  | :--- | :--- |

  | Created Before | - `[created_at][before]=2021-12-30T13:52:18.227Z`<br>-
  `[filters][created_at][conditions][$before][0]=2021-12-30T13:52:18.227Z` |

  | Created After | - `[created_at][after]=2021-12-30T13:52:18.227Z`<br>-
  `[filters][created_at][conditions][$after][0]=2021-12-30T13:52:18.227Z` |

  | Updated Before | - `[updated_at][before]=2021-12-30T13:52:18.227Z`<br>-
  `[filters][updated_at][conditions][$before][0]=2021-12-30T13:52:18.227Z` |

  | Updated After | - `[updated_at][after]=2021-12-30T13:52:18.227Z`<br>-
  `[filters][updated_at][conditions][$after][0]=2021-12-30T13:52:18.227Z` |
api:
  file: voucherify-api.json
  operationId: get-promotions-stacks
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---