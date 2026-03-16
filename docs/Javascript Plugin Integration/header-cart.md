---
title: Header Cart
excerpt: Place Cart Icon in page header
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
# Header Cart

Captina offers a simple mechanism for putting a shopping cart icon in the header of a
page. It shows the number of items in the cart, and when clicked on takes the user to the
store.

This requires just the two lines below for integration on your site.
![]()

Here's what to include:

```html
<script src="/lz_client/base.min.js"></script>
<script type="text/javascript">
    var cp_header_cart_anchor_id = '{id}'; // optional
</script>
<script src="/cp/lz_js/lz_captina_header_cart.js" ></script>
```

As a general rule, you should include it in the footer area of your site. It will
automatically suppress itself on the `/order/` page (the webstore).

You can specify an element for the cart icon via the variable `cp_header_cart_anchor_id`;
otherwise, it will be attached to the document body.