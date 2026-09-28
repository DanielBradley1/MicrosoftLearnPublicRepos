<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/autotaskendpointbackup-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Autotask Endpoint Backup for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Autotask Endpoint Backup with Microsoft Entra ID. When you integrate Autotask Endpoint Backup with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Autotask Endpoint Backup.
- Enable your users to be automatically signed-in to Autotask Endpoint Backup with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Autotask Endpoint Backup single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Autotask Endpoint Backup supports **IDP** initiated SSO.

## Add Autotask Endpoint Backup from the gallery

To configure the integration of Autotask Endpoint Backup into Microsoft Entra ID, you need to add Autotask Endpoint Backup from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Autotask Endpoint Backup** in the search box.
4. Select **Autotask Endpoint Backup** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Autotask Endpoint Backup

Configure and test Microsoft Entra SSO with Autotask Endpoint Backup using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Autotask Endpoint Backup.

To configure and test Microsoft Entra SSO with Autotask Endpoint Backup, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Autotask Endpoint Backup SSO](#configure-autotask-endpoint-backup-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Autotask Endpoint Backup test user](#create-autotask-endpoint-backup-test-user)** - to have a counterpart of B.Simon in Autotask Endpoint Backup that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Autotask Endpoint Backup** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Set up Single Sign-On with SAML** page, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.backup.autotask.net/singlesignon/saml/metadata`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.backup.autotask.net/singlesignon/saml/SSO`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Autotask Endpoint Backup Client support team](https://backup.autotask.net/help/Content/0_HOME/Support_for_End_Clients.htm) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up Autotask Endpoint Backup** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Autotask Endpoint Backup SSO

To configure single sign-on on **Autotask Endpoint Backup** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Autotask Endpoint Backup support team](https://backup.autotask.net/help/Content/0_HOME/Support_for_End_Clients.htm). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Autotask Endpoint Backup test user

In this section, you create a user called Britta Simon in Autotask Endpoint Backup. Work with [Autotask Endpoint Backup support team](https://backup.autotask.net/help/Content/0_HOME/Support_for_End_Clients.htm) to add the users in the Autotask Endpoint Backup platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the Autotask Endpoint Backup for which you set up the SSO.
- You can use Microsoft My Apps. When you select the Autotask Endpoint Backup tile in the My Apps, you should be automatically signed in to the Autotask Endpoint Backup for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Autotask Endpoint Backup you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
