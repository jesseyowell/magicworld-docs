---
title: List Member Rewards
excerpt: >-
  Retrieves the list of rewards that the given customer (identified by
  `member_id`, which is a loyalty card assigned to a particular customer) **can
  get in exchange for loyalty points**.  


  You can use the `affordable_only` parameter to limit the results to rewards
  that the customer can actually afford (only rewards whose price in points is
  not higher than the loyalty points balance on a loyalty card).  


  Please note that rewards that are disabled (i.e. set to `Not Available` in the
  Dashboard) for a given loyalty tier reward mapping will not be returned in
  this endpoint.
api:
  file: voucherify-api.json
  operationId: get-loyalties-members-memberId-rewards
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---