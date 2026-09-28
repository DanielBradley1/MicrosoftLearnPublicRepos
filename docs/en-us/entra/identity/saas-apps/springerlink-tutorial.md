<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/springerlink-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Springer Link for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Springer Link with Microsoft Entra ID. When you integrate Springer Link with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Springer Link.
- Enable your users to be automatically signed-in to Springer Link with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Springer Link single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Springer Link supports **SP and IDP** initiated SSO

## Adding Springer Link from the gallery

To configure the integration of Springer Link into Microsoft Entra ID, you need to add Springer Link from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Springer Link** in the search box.
4. Select **Springer Link** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO

Configure and test Microsoft Entra SSO with Springer Link using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Springer Link.

To configure and test Microsoft Entra SSO with Springer Link, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   - **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
   - **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.

2. **[Configure Springer Link SSO](#configure-springer-link-sso)** - to configure the Single Sign-On settings on application side.
3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Springer Link** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the edit/pen icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, enter the values for the following fields:

   a. In the **Identifier** text box, type the URL: `https://fsso.springer.com`

   b. In the **Reply URL** text box, type the URL: `https://fsso.springer.com/federation/Consumer/metaAlias/SpringerServiceProvider`

   c. Select **Set additional URLs**.

   d. In the **Relay State** text box, type the URL: `https://link.springer.com`
6. If you wish to configure the application in **SP** initiated mode, perform the following step:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://fsso.springer.com/saml/login?idp=<entityID>&targetUrl=https://link.springer.com`

   Note

   The Sign-on URL value isn't real. Update the value with the actual Sign-On URL. `<entityID>` is the Microsoft Entra Identifier copied from the **Set up Springer Link** section, described later in article. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select the copy icon to copy **App Federation Metadata Url** and save it on your computer.

   ![The metadata download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy_metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Springer Link SSO

To configure single sign-on on the **Springer Link** side, you need to send the copied **App Federation Metadata Url** to the [Springer Link support team](mailto:onlineservice@springernature.com). The Springer link support team uses this URL to set up the SAML SSO connection properly on both sides.

### Create Springer Link test user

In this section, you create a user called Britta Simon in Springer Link. Work with [Springer Link support team](mailto:onlineservice@springernature.com) to add the users in the Springer Link platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Springer Link Sign on URL where you can initiate the login flow.
- Go to Springer Link Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Springer Link for which you set up the SSO

You can also use Microsoft Access Panel to test the application in any mode. When you select the Springer Link tile in the Access Panel, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Springer Link for which you set up the SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Springer Link you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).

- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
