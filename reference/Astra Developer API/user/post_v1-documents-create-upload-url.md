---
title: Create Document Upload URL for User
excerpt: >-
  > 📘

  > 

  > You can place the bearer `access_token` for a specific user into the
  Authentication section of this documentation 👉.


  This endpoint handles the upload of a government-issued ID for users who have
  the document status and must upload additional documentation to verify their
  identity. There are three types of acceptable documents: license, ID card, or
  passport. There are three types of acceptable document extensions: jpg, jpeg,
  or png. The document must be in color.


  > 📘

  > 

  >  After you receive the file upload URL, you should submit the file to the
  URL: `curl -X PUT --header "Content-Type:application/octet-stream"
  --data-binary @your_file_name.jpg "your_upload_url"`


  > 📘

  > 

  > For the Business Verification flow, a Business may also be placed into a
  `document` status. For Business types, we allow `.pdf` extensions for document
  uploads. In this scenario the `document_type` needs to be set to `other`.
api:
  file: astra-developer-api.json
  operationId: post_v1-documents-create-upload-url
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---