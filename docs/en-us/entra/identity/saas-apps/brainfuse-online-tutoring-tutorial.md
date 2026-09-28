<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/brainfuse-online-tutoring-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Brainfuse Online Tutoring for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Brainfuse Online Tutoring with Microsoft Entra ID. This app provides single sign-on integration to Brainfuse Live Tutoring. You must be a subscriber to use the app. When you integrate Brainfuse Online Tutoring with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Brainfuse Online Tutoring.
- Enable your users to be automatically signed-in to Brainfuse Online Tutoring with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for Brainfuse Online Tutoring in a test environment. Brainfuse Online Tutoring supports **SP** initiated single sign-on.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Prerequisites

To integrate Microsoft Entra ID with Brainfuse Online Tutoring, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Brainfuse Online Tutoring single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the Brainfuse Online Tutoring application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add Brainfuse Online Tutoring from the Microsoft Entra gallery

Add Brainfuse Online Tutoring from the Microsoft Entra application gallery to configure single sign-on with Brainfuse Online Tutoring. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Brainfuse Online Tutoring** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type the URL: `https://landing.brainfuse.com/shibboleth`

   b. In the **Reply URL** textbox, type the URL: `https://landing.brainfuse.com/Shibboleth.sso/SAML2/POST`

   c. In the **Sign on URL** textbox, type a URL using the following pattern: `https://landing.brainfuse.com/saml.asp?oauth_consumer_key=<ID>`

   Note

   This value isn't real. Update this value with the actual Sign on URL. Contact [Brainfuse Online Tutoring support team](mailto:support@brainfuse.com) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. Brainfuse Online Tutoring application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Attributes")

7. In addition to above, Brainfuse Online Tutoring application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | mail | user.mail |
   | primarysid | user.userprincipalname |
8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

## Configure Brainfuse Online Tutoring SSO

To configure single sign-on on **Brainfuse Online Tutoring** side, you need to send the **App Federation Metadata Url** to [Brainfuse Online Tutoring support team](mailto:support@brainfuse.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Brainfuse Online Tutoring test user

In this section, you create a user called Britta Simon at Brainfuse Online Tutoring. Work with [Brainfuse Online Tutoring support team](mailto:support@brainfuse.com) to add the users in the Brainfuse Online Tutoring platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Brainfuse Online Tutoring Sign-on URL where you can initiate the login flow.
- Go to Brainfuse Online Tutoring Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Brainfuse Online Tutoring tile in the My Apps, this option redirects to Brainfuse Online Tutoring Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure Brainfuse Online Tutoring you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
