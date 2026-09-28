<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/scclifecycle-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure SCC LifeCycle for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate SCC LifeCycle with Microsoft Entra ID. When you integrate SCC LifeCycle with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to SCC LifeCycle.
- Enable your users to be automatically signed-in to SCC LifeCycle with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- SCC LifeCycle single sign-on enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- SCC LifeCycle supports **SP** initiated SSO.

## Add SCC LifeCycle from the gallery

To configure the integration of SCC LifeCycle into Microsoft Entra ID, you need to add SCC LifeCycle from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **SCC LifeCycle** in the search box.
4. Select **SCC LifeCycle** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for SCC LifeCycle

Configure and test Microsoft Entra SSO with SCC LifeCycle using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in SCC LifeCycle.

To configure and test Microsoft Entra SSO with SCC LifeCycle, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure SCC LifeCycle SSO](#configure-scc-lifecycle-sso)** - to configure the single sign-on settings on application side.

   1. **[Create SCC LifeCycle test user](#create-scc-lifecycle-test-user)** - to have a counterpart of B.Simon in SCC LifeCycle that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **SCC LifeCycle** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using one of the following patterns:

   | **Identifier** |
   | --- |
   | `https://bs1.scc.com/<entity>` |
   | `https://lifecycle.scc.com/<entity>` |


   b. In the **Sign on URL** text box, type a URL using the following pattern: `https://<sub-domain>.scc.com/ic7/welcome/customer/PICTtest.aspx`


   Note


   These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [SCC LifeCycle Client support team](mailto:lifecycle.support@scc.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up SCC LifeCycle** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure SCC LifeCycle SSO

To configure single sign-on on **SCC LifeCycle** side, you need to send the downloaded **Metadata XML** and appropriate copied URLs from the application configuration to [SCC LifeCycle support team](mailto:lifecycle.support@scc.com). They set this setting to have the SAML SSO connection set properly on both sides.

Note

Single sign-on has to be enabled by the [SCC LifeCycle support team](mailto:lifecycle.support@scc.com).

### Create SCC LifeCycle test user

In order to enable Microsoft Entra users to log into SCC LifeCycle, they must be provisioned into SCC LifeCycle. There's no action item for you to configure user provisioning to SCC LifeCycle.

When an assigned user tries to log into SCC LifeCycle, an SCC LifeCycle account is automatically created if necessary.

Note

The Microsoft Entra account holder receives an email and follows a link to confirm their account before it becomes active.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to SCC LifeCycle Sign-on URL where you can initiate the login flow.
- Go to SCC LifeCycle Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the SCC LifeCycle tile in the My Apps, this option redirects to SCC LifeCycle Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure SCC LifeCycle you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
