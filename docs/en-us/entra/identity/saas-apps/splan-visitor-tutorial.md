<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/splan-visitor-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-19 -->

# Configure Splan Visitor for Single sign-on in Microsoft Entra ID

In this article, you learn how to integrate Splan Visitor with Microsoft Entra ID. When you integrate Splan Visitor with Microsoft Entra ID, you can:

- Use Microsoft Entra ID to control who has access to Splan Visitor.
- Enable users to be automatically signed in to Splan Visitor with their Microsoft Entra accounts.
- Manage your accounts in one central location, the Azure portal.

Splan Visitor is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A Splan Visitor single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Splan Visitor supports IdP-initiated SSO.

## Add Splan Visitor from the gallery

To configure the integration of Splan Visitor into Microsoft Entra ID, add Splan Visitor from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, enter **Splan Visitor** in the search box.
4. Select **Splan Visitor** from the results panel, and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Splan Visitor

Configure and test Microsoft Entra SSO with Splan Visitor by using a test user named **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Splan Visitor.

To configure and test Microsoft Entra SSO with Splan Visitor, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** to test Microsoft Entra single sign-on with test user B.Simon.
   2. **Assign the Microsoft Entra test user** to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Splan Visitor SSO](#configure-splan-visitor-sso)** to configure the single sign-on settings with Splan Visitor.

   1. **[Create a Splan Visitor test user](#create-a-splan-visitor-test-user)** to have a counterpart of B.Simon in Splan Visitor that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Azure portal:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Splan Visitor** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up Single Sign-On with SAML** page, select the **pencil** icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot highlighting the edit/pen icon for Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, the application is preconfigured and the necessary URLs are prepopulated with Azure. Select the **Save** button to save the configuration.
6. On the **Set up Single Sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML**. Select **Download** to download the certificate and save it to your computer.

   ![Screenshot highlighting the Federation Metadata XML download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up Splan Visitor** section, copy the appropriate URL or URLs based on your requirement.

   ![Screenshot highlighting the configuration URLs section.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Splan Visitor SSO

To configure single sign-on with Splan Visitor, send the **Federation Metadata XML** that you downloaded and appropriate copied URLs to the [Splan Visitor support team](mailto:support@splan.com). This ensures that the SAML SSO connection is set properly on both sides.

### Create a Splan Visitor test user

Create a test user named **Britta Simon** in Splan Visitor. Work with the [Splan Visitor support team](mailto:support@splan.com) to add the user to Splan Visitor. You must create and activate the user before you use single sign-on.

## Test SSO

Test your Microsoft Entra single sign-on configuration with one of the following options:

- **Azure portal**: Select **Test this application** to automatically sign in to the Splan Visitor for which you set up SSO.
- **Microsoft My Apps portal**: Select the **Splan Visitor** tile to automatically sign in to the Splan Visitor for which you set up SSO. For more information about the My Apps portal, see [Sign in and start apps from the My Apps portal](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

After you configure Splan Visitor, you can [learn how to enforce session controls in Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app). Session controls help protect exfiltration and infiltration of your organization's sensitive data in real time. Session controls extend from Conditional Access.
