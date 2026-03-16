---
title: List Validation Rules' Assignment(s)
excerpt: >-
  List all validation rules' assignments or filter the results using the related
  object ID or the validation rule ID query parameters. 


  ## How to retrieve specific validaiton rule assignments(s)


  ### Related object ID


  To find an assignment for a particular resource, you can use the ID of the
  object to which the validation rule was assigned. This could be, for example,
  an ID of a: voucher, campaign, distribution, reward assignment, earning rule,
  promotion tier.  



  <!--

  title: "Request"

  lineNumbers: true

  -->

  ```curl

  curl -X GET \
    -H "X-App-Id: c70a6f00-cf91-4756-9df5-47628850002b" \
    -H "X-App-Token: 3266b9f8-e246-4f79-bdf0-833929b1380c" \
    -H "Content-Type: application/json" \
    https://api.voucherify.io/v1/validation-rules-assignments?related_object_id=promo_kJliy076IuJYtuYWSHE9fSuT
  ```

  <!--

  title: "Response"

  lineNumbers: true

  -->

  ```json

  {
      "object": "list",
      "data_ref": "data",
      "data": [
          {
              "id": "asgm_tZaqxeO8gP4q91jG",
              "rule_id": "val_WB6ETAiFztw5",
              "related_object_id": "promo_kJliy076IuJYtuYWSHE9fSuT",
              "related_object_type": "promotion_tier",
              "created_at": "2022-08-10T10:30:39.986Z",
              "object": "validation_rules_assignment"
          }
      ],
      "total": 1
  }

  ```


  ### Validation rule ID


  You can use the validation rule ID to find assignment(s) for a specific
  validation rule.



  <!--

  title: "Request"

  lineNumbers: true

  -->

  ```curl

  curl -X GET \
    -H "X-App-Id: c70a6f00-cf91-4756-9df5-47628850002b" \
    -H "X-App-Token: 3266b9f8-e246-4f79-bdf0-833929b1380c" \
    -H "Content-Type: application/json" \
    https://api.voucherify.io/v1/validation-rules-assignments?rule=val_ZEZmA9oit8aU
  ```

  <!--

  title: "Response"

  lineNumbers: true

  -->

  ```json

  {
      "object": "list",
      "data_ref": "data",
      "data": [
          {
              "id": "asgm_vef0G6d9Al0rABxq",
              "rule_id": "val_ZEZmA9oit8aU",
              "related_object_id": "camp_rRsfatlwN7unSeUIJDCYedal",
              "related_object_type": "campaign",
              "created_at": "2022-06-29T11:43:52.953Z",
              "object": "validation_rules_assignment"
          },
          {
              "id": "asgm_sFV4wEFvldwIvgfb",
              "rule_id": "val_ZEZmA9oit8aU",
              "related_object_id": "distr_9QKI02wqgjWyvZXeQkFEPmkkYe",
              "related_object_type": "distribution",
              "created_at": "2022-06-29T11:41:07.680Z",
              "object": "validation_rules_assignment"
          },
          {
              "id": "asgm_69Qifyv6UZynFIIQ",
              "rule_id": "val_ZEZmA9oit8aU",
              "related_object_id": "promo_g83qUzYZpfX0OMAFOVoQuOYG",
              "related_object_type": "promotion_tier",
              "created_at": "2022-06-29T11:29:41.906Z",
              "object": "validation_rules_assignment"
          }
      ],
      "total": 3
  }

  ```
api:
  file: voucherify-api.json
  operationId: get-validation-rules-assignments
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---