<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/eventfinity-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Eventfinity for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Eventfinity with Microsoft Entra ID. When you integrate Eventfinity with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Eventfinity.
- Enable your users to be automatically signed-in to Eventfinity with their Microsoft Entra accounts.
- Manage your accounts in one central location.

To learn more about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Eventfinity single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Eventfinity supports **SP and IDP** initiated SSO
- Once you configure Eventfinity you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Adding Eventfinity from the gallery

To configure the integration of Eventfinity into Microsoft Entra ID, you need to add Eventfinity from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Eventfinity** in the search box.
4. Select **Eventfinity** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra single sign-on for Eventfinity

Configure and test Microsoft Entra SSO with Eventfinity using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Eventfinity.

To configure and test Microsoft Entra SSO with Eventfinity, complete the following building blocks:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Eventfinity SSO](#configure-eventfinity-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Eventfinity test user](#create-eventfinity-test-user)** - to have a counterpart of B.Simon in Eventfinity that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Eventfinity** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the edit/pen icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, enter the values for the following fields:

   In the **Reply URL** text box, type a URL using the following pattern: `https://auth.eventfinity.co/saml/<ID>/acs`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://auth.eventfinity.co/saml/<ID>/sso`

   Note

   These values aren't real. Update these values with the actual Reply URL and Sign-On URL. Contact [Eventfinity Client support team](mailto:help@eventfinity.co) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Eventfinity SSO

To configure single sign-on on **Eventfinity** side, you need to send the **App Federation Metadata Url** to [Eventfinity support team](mailto:help@eventfinity.co). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Eventfinity test user

In this section, you create a user called B.Simon in Eventfinity. Work with [Eventfinity support team](mailto:help@eventfinity.co) to add the users in the Eventfinity platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.

When you select the Eventfinity tile in the Access Panel, you should be automatically signed in to the Eventfinity for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
- [What is session control in Microsoft Defender for Cloud Apps?](https://learn.microsoft.com/en-us/cloud-app-security/proxy-intro-aad)
