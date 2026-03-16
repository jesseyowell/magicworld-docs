---
title: Mailing List / Contact Form
excerpt: Add a contact us / mailing list signup form to any page
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: noindex
next:
  description: ''
---
# Mailing List / Contact Us

You can easily add a contact us / mailing list signup form to any page, as follows

1. create a container:

```html
<div id="captina_mailing_list_signup_form" class="mailing-list"></div>
```

2. include these files:

```html
<script src="/lz_client/base.min.js"></script>
<script src="/cp/lz_js/lz_captina_mailing_list_signup.js"></script>
```

3. optionally include this file if you want "pretty" error and success messages:

```html
<script src="/cp/lz_js/lz_alert_dialogs.js"></script>
```

4. set the parameters and trigger the creation of the form (the values are the defaults)

```html
<script type="text/javascript">
    CaptinaMailingListDef = {
        table_or_div: "table", // table | div
        display_mode: "inline", // inline | popup
        contact_btn_label: "[string]",
        signup_btn_label: "[string]",
        success_url: "[optional]",
        image_url: "[url for image]",
        image_title: "[string]",
        name_label: "Name:",
        name_placeholder: "Name \*",
        email_label: "Email:",
        email_placeholder: "Email Address \*",
        postal_field: "show",
        postal_label: "Zip:",
        postal_placeholder: "Zip Code",
        postal_required: false,
        phone_field: "show",
        phone_label: "Phone:",
        phone_placeholder: "Phone",
        phone_required: false,
        note_field: "show",
        note_label: "Note:",
        note_placeholder: "Note",
        note_required: false,
        contact_optin_field: "show",
        contact_optin_label: "join the mailing list",
        contact_optin_default: "checked",
        spambot_field: "show",
        spambot_label: "I'm a human",
        signup_field: "show",
        signup_label: "add me to your mailing list"
    };
</script>
```

## Parameter Notes

The `table_or_div` element is required. When set to "table", the mailing list form will be\
constructed as an HTML table; if set to "div", the form will be built using divs.

* ☞ In general, it is easier to style the elements with divs.

The `display_mode` element dictates how the form will be rendered. If set to "inline" or\
omitted, then the form will be displayed on the page; if set to "popup", then the form\
will be hidden, and buttons will be displayed for mailing-list signup and/or contact\
actions, depending on whether the elements `contact_btn_label` and `signup_btn_label` are\
present and populated. The contents of the form will vary depending on which button is\
clicked; for example, the note field will be suppressed for mailing-list-signup requests.

All fields are easily styled according to their id or class:

```
            table:               `#captina_mlsf_table`
            row container:       `.captina_mlsf_th`
            label fields:        `.captina_mlsf_label`
            input fields:        `.lz_textbox`
            textareas:           `.lz_textarea`
            signup:              `(see below)`
            spambot:             `(see below)`
```

The `success_url` element is optional. If present and populated, the browser will be\
redirected to that url upon a successful completion of a signup.

The `postal` and `phone` fields are optional; if present, the "`_required`" element\
dictates whether the user can skip them.

The `note` field is also optional; if populated the contents will be stored as a note in\
the person's *CRM* in the database, and included in the notification email (see below).\
Thus, the form serves double-duty as a "join mailing list" function as well as "contact\
us".

The `image_url` parameter is optional. If present, a div will be created (it will be the\
first item in the overall form so that its placement can be readily controlled) with the\
class name `mlsf_image_wrapper`, and the image will be placed inside it. The value of\
`image_url` will be the `src` parameter of the image; `image_title` will be the `title` parameter.

If a `label` element is blank, then no label will be created; if it is not present, then the\
default label will be used.

If a `placeholder` element is blank, then there will be no placeholder; if it is not\
present, then the default will be used.

If the `submit_label` element is present, the string associated with it will be used for the\
action button; the default is "sign up";

If the `signup` element is missing, or checked, then the person will be added to the mailing\
list; if it is present and unchecked, the person will not be added.

The optional `contact_optin` element only applies to Contact Us usage. It shows a checkbox\
that a person submitting a question can use to join/opt-out of the mailing list.

* ☞ We recommend that you include the spambot section; it uses as simple checkbox that has\
  been proven effective against most spambots.

## Pop-up

The pop-up will have the following layout:

```html
<div class="captina_mailing_list_signup_form">
    <div class="captina_mlsf_wrapper mlsf_popup">
        <div class="mlsf_inner_wrapper">
            <div class="mlsf_image_wrapper">
                <img/>
            </div>
            <div class="closeButtonX"></div>
            <div class="mlsf_form_wrapper">
                <h3></h3>
                <div id="captina_mlsf_table">
                    <!-- form fields -->
                </div>
                <span class="captina_mlsf_button_span">
                <button>{submit}</button>
            </span>
            </div>
        </div>
    </div>
</div>
```

All of these elements come pre-styled; you can add CSS to match your site's design. Final\
styling is governed by the Site-wide plugin stylesheet found under\
Administration->Stylesheets for Plugins.

## Confirmation

If a submission is successful, an email will be sent to the person submitting the request.\
That email will use parameters and elements specified on the Administration page.

The templates are found in Email Templates for Mailing list signup, and the subject line\
found under Email Addressing.

The "from" address will be the Email Marketing from name/address (Email Addressing).

If the BCC flag for list-welcomes is set (Email Management), the welcome email will be\
BCC'd to the BCC address for customer emails (Email Addressing).

Copyright Captina LLC                                                                           Support: (707) 324-3123
