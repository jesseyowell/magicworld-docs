---
title: List Publications
excerpt: >-
  Retrieve a list of publications. To return a **particular** publication, you
  can use the `source_id` query parameter and provide the `source_id` of the
  publication you are looking for specifically.


  ## Pagination


  <!-- theme: warning -->

  > 🚧 Important!

  >

  > If you want to scroll through a huge set of records, it is recommended to
  use the <!-- [Exports
  API](OpenAPI.json/components/schemas/16_obj_export_object) -->[Exports
  API](ref:create-export). This API will return an error `page_over_limit` if
  you reach a page above 1000.


  ## Filter Query


  The `filters` query parameter allows for joining multiple parameters with
  logical operators. The syntax looks as follows:


  <!--

  title: "Filter template"

  -->

  ```url

  filters[<field_name>][conditions][<operator>][<index>]=<value>

  ```


  ### Operators:


  <!--

  title: "Operators"

  -->

  ```
      "$in"
      "$not_in"
      "$is"
      "$is_not"
      "$has_value"
      "$is_unknown"
      "$contains"
      "$starts_with"
      "$ends_with"
      "$more_than"
      "$less_than"
      "$more_than_equal"
      "$less_than_equal"
  ```


  ### Examples


  <!--

  title: "Example 1 - List publications of a given customer"

  -->

  ```url

  GET
  /v1/publications?filters[customer_id][conditions][$is][0]=cust_lUET6gRpO5Wxlg5p2j2gRCgL

  ```

  <!--

  title: "Example 2 - List publications of 2 customers"

  -->

  ```url

  GET
  /v1/publications?filters[customer_id][conditions][$in][0]=cust_lUET6gRpO5Wxlg5p2j2gRCgL&filters[customer_id][conditions][$in][1]=cust_aR7NfHusxT7PdTMAKMfWDXnc

  ```

  <!--

  title: "Example 3 - List publications of 2 customers using junction operator"

  -->

  ```url

  GET
  /v1/publications?filters[customer_id][conditions][$is][0]=cust_lUET6gRpO5Wxlg5p2j2gRCgL&filters[customer_id][conditions][$is][1]=cust_aR7NfHusxT7PdTMAKMfWDXnc&filters[junction]=OR

  ```
api:
  file: voucherify-api.json
  operationId: get-publications
deprecated: false
hidden: false
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---