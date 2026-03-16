---
title: Create a Card for a User
excerpt: >-
  > 📘

  > 

  > You can place the bearer `access_token` for a specific user into the
  Authentication section of this documentation 👉.


  Cards can be created directly through the API using this PCI-compliant
  endpoint if the card is issued from your company.


  Cards can also be created through the OAuth Module by selecting the **Connect
  New Debit Card** button. If the card being created is not issued from your
  company, it must be created through the OAuth module, which is Payment Card
  Industry (PCI) compliant. Astra is PCI certified.


  For Unit customers, please reference their technical documentation below to
  learn more about enabling card to card payments. [Enabling Card to Card
  Payments with Unit & Astra](https://guides.unit.co/partnerships/astra/)


  > 🚧

  > 

  > This resource requires the use of the secure endpoint.

  >

  > | Environment | Secure Endpoint                                   |

  > |-------------|---------------------------------------------------|

  > | Production  | https://secure.api.astra.finance/cards            |

  > | Sandbox     | https://secure.api-sandbox.astra.finance/v1/cards |
api:
  file: astra-developer-api.json
  operationId: post_v1-cards
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---