---
title: Challenge dispute
excerpt: >-
  Submits evidence uploaded to this dispute to Cash App Pay for review.


  Once Cash App Pay reviews the dispute, a final decision will be reached and
  funds will be settled appropriately. If this endpoint is not called by the
  `response_due_at` timestamp, the merchant will automatically "lose" the
  dispute.


  > Challenging a dispute does not guarantee that the merchant will "win" it. It
  only means that it will be reviewed, instead of being automatically accepted
  by the merchant.


  **This endpoint is not rate limited.**


  Scopes: `DISPUTES_WRITE`
api:
  file: network-api.json
  operationId: challenge-dispute
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---