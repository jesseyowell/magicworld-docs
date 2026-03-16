---
title: Privacy Policy
excerpt: Place your privacy policy site-wide
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
# Privacy Policy

Every website should have a Privacy Policy. In a growing number of states, it's legally\
required.

CompleteDTC offers a default privacy policy, but you should strongly consider creating\
your own. You can do so via **Company Privacy Policy** in Administration->Miscellaneous.

This is a very lightweight plugin, requiring just two lines for integration on your site.\
As a general rule, you should include it in the footer area of your site so that it shows\
on every page.

Here's what to include:

```html
<script src="/lz_client/base.min.js"></script>
<script src="/cp/lz_js/lz_captina_privacy_policy.js" ></script>
```

In addition, you need to create a link, as follows:

```html
<span onclick="displayPrivacyPolicy();">Privacy Policy</span>
```

Note that the wrapper can be a `<div>`, `<span>`, etc. It is a good idea to set the CSS `cursor`\
attribute for the wrapper to "pointer".
