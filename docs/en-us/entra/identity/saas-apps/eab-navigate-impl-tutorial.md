<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/eab-navigate-impl-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure EAB Implementation for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate EAB Implementation with Microsoft Entra ID. When you integrate EAB Implementation with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to EAB Implementation.
- Enable your users to be automatically signed-in to EAB Implementation with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- EAB Implementation single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- EAB Implementation supports **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Adding EAB Implementation from the gallery

To configure the integration of EAB Implementation into Microsoft Entra ID, you need to add EAB Implementation from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **EAB Implementation** in the search box.
4. Select **EAB Implementation** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for EAB Implementation

Configure and test Microsoft Entra SSO with EAB Implementation using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in EAB Implementation.

To configure and test Microsoft Entra SSO with EAB Implementation, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure EAB Implementation SSO](#configure-eab-implementation-sso)** - to configure the single sign-on settings on application side.

   1. **[Create EAB Implementation test user](#create-eab-implementation-test-user)** - to have a counterpart of B.Simon in EAB Implementation that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **EAB Implementation** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, enter the values for the following fields:

   a. In the **Identifier \(Entity ID\)** text box, enter exactly the following value: `https://impl.bouncer.eab.com`

   b. In the **Reply URL \(Assertion Consumer Service URL\)** text box, enter both the following values as separate rows:

   | Reply URL |
   | --- |
   | `https://impl.bouncer.eab.com/sso/saml2/acs` |
   | `https://impl.bouncer.eab.com/sso/saml2/acs/` |
   |  |


   c. In the **Sign-on URL** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.navigate.impl.eab.com/`


   Note


   The value isn't real. Update the value with the actual Sign-On URL. Contact [EAB Implementation Client support team](mailto:EABTechSupport@eab.com) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure EAB Implementation SSO

To configure single sign-on on **EAB Implementation** side, you need to send the **App Federation Metadata Url** to [EAB Implementation support team](mailto:EABTechSupport@eab.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create EAB Implementation test user

In this section, you create a user called B.Simon in EAB Implementation. Work with [EAB Implementation support team](mailto:EABTechSupport@eab.com) to add the users in the EAB Implementation platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to EAB Implementation Sign-on URL where you can initiate the login flow.
- Go to EAB Implementation Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the EAB Implementation tile in the My Apps, this option redirects to EAB Implementation Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure EAB Implementation you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
