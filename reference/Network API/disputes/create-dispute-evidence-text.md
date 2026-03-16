---
title: Create dispute evidence text
excerpt: >-
  Creates a piece of evidence for the given dispute from a blob of plain text,
  which can then be submitted with the [ChallengeDispute](ref:challenge-dispute)
  endpoint.


  If you have more than 500 characters of text to submit as evidence, split it
  into multiple pieces where possible.


  > **Note:** Uploading evidence does not challenge the dispute. Make sure to
  call the [ChallengeDispute](ref:challenge-dispute) endpoint before the
  `response_due_at` timestamp, or else the merchant will automatically "lose"
  the dispute.


  **This endpoint is not rate limited.**


  Scopes: `DISPUTES_WRITE`
api:
  file: network-api.json
  operationId: create-dispute-evidence-text
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---