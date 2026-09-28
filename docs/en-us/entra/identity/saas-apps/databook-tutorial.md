<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/databook-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Databook for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Databook with Microsoft Entra ID. Databook is a customer intelligence platform that provides insights into a company's financial & strategic priorities and maps best-fit Microsoft solutions to deliver high impact recommendations. When you integrate Databook with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Databook.
- Enable your users to be automatically signed-in to Databook with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for Databook in a test environment. Databook supports **SP** and **IDP** initiated single sign-on and also supports **Just In Time** user provisioning.

## Prerequisites

To integrate Microsoft Entra ID with Databook, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Databook single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the Databook application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add Databook from the Microsoft Entra gallery

Add Databook from the Microsoft Entra application gallery to configure single sign-on with Databook. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Databook** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type a value using the following pattern: `urn:auth0:databook:<CustomerID>`

   b. In the **Reply URL** textbox, type a URL using the following pattern: `https://databook.auth0.com/login/callback?connection=<CustomerID>`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign on URL** textbox, type a URL using the following pattern: `https://databook.auth0.com/login?client=<ID>&connection=<CustomerID>`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [Databook Client support team](mailto:info@trydatabook.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. Databook application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Attributes")

8. In addition to above, Databook application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | email | user.mail |
   | firstName | user.givenname |
   | lastName | user.surname |
   | grouptag | user.groups |
9. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

## Configure Databook SSO

To configure single sign-on on **Databook** side, you need to send the **App Federation Metadata Url** to [Databook support team](mailto:info@trydatabook.com). The support team will use the copied URLs to configure the single sign-on on the application.

### Create Databook test user

In this section, a user called B.Simon is created in Databook. Databook supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Databook, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Databook Sign-on URL where you can initiate the login flow.
- Go to Databook Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Databook for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Databook tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Databook for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure Databook you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
