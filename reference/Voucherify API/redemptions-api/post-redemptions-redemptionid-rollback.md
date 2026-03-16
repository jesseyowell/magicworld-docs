---
title: Rollback Redemption
excerpt: >-
  Your business logic may include a case when you need to undo a redemption. You
  can revert a redemption by calling this API endpoint. 

   ## Effect 
  The operation 

  - creates a rollback entry in voucher's redemption history
  (`redemption.redemption_entries`) and 

  - gives 1 redemption back to the pool (decreases `redeemed_quantity` by 1). 

  ## Returned funds 

  In case of *gift card vouchers*, this method returns funds back according to
  the source redemption. In case of *loyalty card vouchers*, this method returns
  points back according to the source redemption.
api:
  file: voucherify-api.json
  operationId: post-redemptions-redemptionId-rollback
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---