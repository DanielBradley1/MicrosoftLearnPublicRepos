<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/keeperpasswordmanager-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Configure Keeper Password Manager for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Keeper Password Manager with Microsoft Entra ID. When you integrate Keeper Password Manager with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Keeper Password Manager.
- Enable your users to be automatically signed-in to Keeper Password Manager with their Microsoft Entra accounts.
- Manage your accounts in one central location.

Keeper Password Manager is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

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

- Keeper Password Manager single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Keeper Password Manager supports SP-initiated SSO.
- Keeper Password Manager supports [**Automated** user provisioning and deprovisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/keeper-password-manager-digitalvault-provisioning-tutorial) \(recommended\).
- Keeper Password Manager supports just-in-time user provisioning.

## Add Keeper Password Manager from the gallery

To configure the integration of Keeper Password Manager into Microsoft Entra ID, add the application from the gallery to your list of managed software as a service \(SaaS\) apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In **Add from the gallery**, type **Keeper Password Manager** in the search box.
4. Select **Keeper Password Manager** from results panel, and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Keeper Password Manager

Configure and test Microsoft Entra SSO with Keeper Password Manager by using a test user called **B.Simon**. For SSO to work, you need to establish a linked relationship between a Microsoft Entra user and the related user in Keeper Password Manager.

To configure and test Microsoft Entra SSO with Keeper Password Manager:

1. [Configure Microsoft Entra SSO](#configure-azure-ad-sso) to enable your users to use this feature.

   1. Create a Microsoft Entra test user to test Microsoft Entra single sign-on with Britta Simon.
   2. Assign the Microsoft Entra test user to enable Britta Simon to use Microsoft Entra single sign-on.

2. [Configure Keeper Password Manager SSO](#configure-keeper-password-manager-sso) to configure the SSO settings on the application side.

   1. [Create a Keeper Password Manager test user](#create-a-keeper-password-manager-test-user) to have a counterpart of Britta Simon in Keeper Password Manager linked to the Microsoft Entra representation of the user.

3. [Test SSO](#test-sso) to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Keeper Password Manager** application integration page, find the **Manage** section. Select **single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot of Set up Single Sign-On with SAML, with pencil icon highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, perform the following steps:

   a. For **Identifier \(Entity ID\)**, type a URL using one of the following patterns:

   - For cloud SSO: `https://keepersecurity.com/api/rest/sso/saml/<CLOUD_INSTANCE_ID>`
   - For on-premises SSO: `https://<KEEPER_FQDN>/sso-connect`


   b. For **Reply URL**, type a URL using one of the following patterns:


   - For cloud SSO: `https://keepersecurity.com/api/rest/sso/saml/sso/<CLOUD_INSTANCE_ID>`
   - For on-premises SSO: `https://<KEEPER_FQDN>/sso-connect/saml/sso`


   c. For **Sign on URL**, type a URL using one of the following patterns:


   - For cloud SSO: `https://keepersecurity.com/api/rest/sso/ext_login/<CLOUD_INSTANCE_ID>`
   - For on-premises SSO: `https://<KEEPER_FQDN>/sso-connect/saml/login`


   d. For **Sign out URL**, type a URL using one of the following patterns:


   - For cloud SSO: `https://keepersecurity.com/api/rest/sso/saml/slo/<CLOUD_INSTANCE_ID>`
   - There's no configuration for on-premises SSO.


   Note


   These values aren't real. Update these values with the actual Identifier,Reply URL and Sign on URL. To get these values, contact the [Keeper Password Manager Client support team](https://keepersecurity.com/contact.html). You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. The Keeper Password Manager application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot of User Attributes & Claims.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

7. In addition, the Keeper Password Manager application expects a few more attributes to be passed back in SAML response. These are shown in the following table. These attributes are also pre-populated, but you can review them per your requirements.
   | Name | Source attribute |
   | --- | --- |
   | First | user.givenname |
   | Last | user.surname |
   | Email | user.mail |
8. On **Set up Single Sign-On with SAML**, in the **SAML Signing Certificate** section, select **Download**. This downloads **Federation Metadata XML** from the options per your requirement, and saves it on your computer.

   ![Screenshot of SAML Signing Certificate with Download highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

9. On **Set up Keeper Password Manager**, copy the appropriate URLs, per your requirement.

   ![Screenshot of Set up Keeper Password Manager with URLs highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Keeper Password Manager SSO

To configure SSO for the app, see the guidelines in the [Keeper support guide](https://docs.keeper.io/sso-connect-cloud/identity-provider-setup/azure-o365-keeper).

### Create a Keeper Password Manager test user

To enable Microsoft Entra users to sign in to Keeper Password Manager, you must provision them. The application supports just-in-time user provisioning, and after authentication users are created in the application automatically. If you want to set up users manually, contact [Keeper support](https://keepersecurity.com/contact.html).

Note

Keeper Password Manager also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/keeper-password-manager-digitalvault-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Keeper Password Manager Sign-on URL where you can initiate the login flow.
- Go to Keeper Password Manager Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Keeper Password Manager tile in the My Apps, this option redirects to Keeper Password Manager Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

After you configure Keeper Password Manager, you can enforce session control. This protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. For more information, see [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
