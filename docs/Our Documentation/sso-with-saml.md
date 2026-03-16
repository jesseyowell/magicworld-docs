---
title: SSO with SAML
excerpt: ''
deprecated: false
hidden: true
metadata:
  title: ''
  description: ''
  robots: index
next:
  description: ''
---
If you have an identity provider (IDP) that supports SAML 2.0, you can use it with FireHydrant as a single sign-on provider.

## Prerequisites

* You'll need to [reach out to our support team](https://support.firehydrant.com/hc/en-us/requests/new) to enable SSO for your organization
* You will need <Glossary>Owner</Glossary> permissions to configure SSO settings on FireHydrant
* You will need administrative access to your IDP to create a new SAML application and administer users

## Google SSO

Setting up single sign-on with Google enables your G Suite account users to authenticate and access FireHydrant accounts.

1. Follow Google's instructions on [setting up a custom SAML application](https://support.google.com/a/answer/6087519?hl=en) until you get to the **Google Identity Provider details page**.
2. In a separate browser tab, open [FireHydrant's SSO settings page](https://app.firehydrant.io/organizations/sso/settings/edit) and check **Enable SSO**. Three additional fields will appear: IDP Login URL, IDP Issuer, and IDP X509 Certificate. Copy the values from Google into FireHydrant as follows:

| Google Value | FireHydrant Field    |
| :----------- | :------------------- |
| SSO URL      | IDP Login URL        |
| Entity ID    | IDP Issuer           |
| Certificate  | IDP X509 Certificate |

3. (Optional) In the **Domains** section of FireHydrant, you can add the email domain name for your organization.
   1. When users attempt to log in to FireHydrant directly with an email address that matches this domain, FireHydrant will display a note and redirect them to your IDP sign-in.
4. Click **Save** in FireHydrant.
5. In Google, click **Next**. Google prompts you to fill in Service Provider details. For the **ACS URL** and **Entitiy ID** fields, enter `https://app.firehydrant.io/sso/saml/consume`.
6. Enable the **Signed Response** checkbox.
7. Verify that **Primary Email** is selected for the Name ID section. This is how your SSO configuration automatically creates accounts or logs existing users into FireHydrant.
8. For the **Name ID Format** field, select **Email**. Click **Next**.
9. (Optional) On the last step of the Google setup, provide any attribute mappings you'd like to include when users are sent to FireHydrant. These are optional, but we recommend setting the first and last name attributes so when users are provisioned, their names are automatically set correctly in FireHydrant.

   <Image alt="Attribute mapping in Google" align="center" width="400px" src="https://files.readme.io/6b5f39f-image.png">
     Attribute mapping in Google
   </Image>
10. Click **Finish**. This completes your Google SSO setup.

## Okta SSO

> 📘 Note:
>
> When a user is authenticated with Okta, they are automatically added to the organization with a <Glossary>Member</Glossary> role if they do not have an account.
>
> Otherwise, accounts are matched on the email provided by Okta on a successful login. When a user is removed from Okta, they are not automatically removed from FireHydrant.

Our Okta SAML integration is one-way - FireHydrant accounts will be automatically provisioned but not automatically de-provisioned. Users whose accounts are auto-provisioned with Okta are set to the <Glossary>Member</Glossary> role.

1. As an Okta admin, view all applications in the **Applications** tab. Then:
2. Click **Browse App Catalog**
3. Search for the FireHydrant app, click it, and then click **Add Integration**
4. Name your app and click **Next**. This will drop you onto the **Assignments** page.
5. Click into **Sign On** and go to **View SAML setup instructions**.
6. In a separate browser tab, open [FireHydrant's SSO settings page](https://app.firehydrant.io/organizations/sso/settings/edit) and check **Enable SSO**. Enter the IDP Login URL, IDP Issuer, and IDP X509 Certificate details from Step #4 into FireHydrant.
   1. (Optional) Add a domain for SP-initiated logins. When users attempt to log in to FireHydrant directly with an email address that matches this domain, FireHydrant will display a note and redirect them to your IDP sign-in.
7. Enable SSO and save your configuration. This completes the setup for Okta SAML 2.0.

## Generic

1. For other identity providers aside from Google and Okta, you can set up the integration by entering FireHydrant's SAML details as below when creating a new SAML application:
   1. **Consumer URL**: `https://app.firehydrant.io/sso/saml/consume`
   2. **Recipient URL and Audience URL**: Same as the consumer URL
   3. **Audience**: `firehydrant`
   4. **Attribute statements**: **First Name** as `firstName`, **Last Name** as `lastName`
2. After you've created your SAML application, you will then need to configure settings within FireHydrant:
   1. In FireHydrant, navigate to **Settings\> Single Sign On**.
   2. On the Single Sign On page, check the box labeled  **Enable SSO**.
   3. Additional fields appear. In these fields, provide your IDP login URL, IDP issuer, and IDP X509 certificate as generated by your identity provider.
   4. (Optional) If you'd like, you can add **Domains**. When users attempt to log in to FireHydrant directly with an email address that matches this domain, FireHydrant will display a note and redirect them to your IDP sign-in.

## Testing

To test, leave your session in FireHydrant open. Visit your IDP in a new window or tab and attempt to log in with your newly configured integration.

Leaving your FireHydrant session open should prevent you from getting locked out of your account during setup. If you encounter a lockout, submit a ticket on our [contact form](https://support.firehydrant.com/hc/en-us/requests/new) for help.
