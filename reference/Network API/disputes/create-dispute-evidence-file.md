---
title: Create dispute evidence file
excerpt: >-
  Uploads a binary file as a piece of evidence for the given dispute, which can
  then be submitted with the [ChallengeDispute](ref:challenge-dispute) endpoint.


  The file must be one of the supported formats, or else it may not be usable to
  challenge the dispute:


  - `JPEG`

  - `HEIC`

  - `HEIF`

  - `PNG`

  - `PDF`

  - `TIFF`


  > **Note:** Uploading evidence does not challenge the dispute. Make sure to
  call the [ChallengeDispute](ref:challenge-dispute) endpoint before the
  `response_due_at` timestamp, or else the merchant will automatically "lose"
  the dispute.


  **This endpoint is not rate limited.**


  Scopes: `DISPUTES_WRITE`
api:
  file: network-api.json
  operationId: create-dispute-evidence-file
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---