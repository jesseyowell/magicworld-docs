---
title: Club Member Sign-in
excerpt: Site-wide Club Member portal
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
# Club Member Sign-in

There is a dedicated sign-in/sign-up plugin available, but we strongly recommend that you
use the site-wide approach, which you install in the site footer to create a login icon on
every page. The syntax is as follows:

![]()

```html
<script type="text/javascript">
    var ClubLoginPopupJSON = {
        myclub_slug: "/my_club",
        trigger_div: "clp_trigger_div",
        email_placeholder: "your email",
        pwd_placeholder: "password",
        trigger_style: "" // optional
    },
    cp_club_signin_anchor_id = "{id}"; // optional
</script>
<script src="/lz_client/base.min.js"></script>
<script src="/cp/lz_js/lz_captina_club_signin.js"></script>
```

You can change the FontAwesome icon via the `ClubLoginPopupJSON` parameter `fa_class` (the
default is the outlined-user symbol `far fa-user`). You may also include parameters for
`email_prompt` and `pwd_prompt` if you want the pop-up login form to have field labels in
addition to the placeholders.

You can specify an element for the login icon via the variable `cp_club_signin_anchor_id`;
otherwise, it will be attached to the document body.