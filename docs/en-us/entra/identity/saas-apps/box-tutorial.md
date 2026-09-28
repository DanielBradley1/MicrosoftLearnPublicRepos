<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/box-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Configure Box for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Box with Microsoft Entra ID. When you integrate Box with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Box.
- Enable your users to be automatically signed-in to Box with their Microsoft Entra accounts.
- Manage your accounts in one central location.

Box is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

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

- Box single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Box supports **SP** initiated SSO
- Box supports [**Automated** user provisioning and deprovisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/box-userprovisioning-tutorial) \(recommended\)
- Box supports **Just In Time** user provisioning

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Adding Box from the gallery

To configure the integration of Box into Microsoft Entra ID, you need to add Box from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Box** in the search box.
4. Select **Box** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Box

Configure and test Microsoft Entra SSO with Box using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Box.

To configure and test Microsoft Entra SSO with Box, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Box SSO](#configure-box-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Box test user](#create-box-test-user)** - to have a counterpart of B.Simon in Box that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Box** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the edit/pen icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, enter the values for the following fields:

   a. In the **Sign on URL** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.account.box.com`

   b. In the **Identifier \(Entity ID\)** text box, type a URL: `box.net`

   c. In the **Reply URL** text box, type the URL: `https://sso.services.box.net/sp/ACS.saml2`

   Note

   The Sign-on URL value isn't real. Update the value with the actual Sign-On URL. Contact [Box Client support team](https://support.box.com) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. Your Box application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows an example for this. The default value of **Unique User Identifier** is **user.userprincipalname** but Box expects this to be mapped with the user's email address. For that you can use **user.mail** attribute from the list or use the appropriate attribute value based on your organization configuration.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Box SSO

1. In a different web browser window, sign in to your Box company site as an administrator and follow the procedure in [Set up SSO on your own](https://support.box.com).

Note

If you're unable to configure the SSO settings for your Box account, you need to send the downloaded **Federation Metadata XML** to [Box support team](https://support.box.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Box test user

In this section, a user called Britta Simon is created in Box. Box supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Box, a new one is created after authentication.

Note

If you need to create a user manually, contact [Box support team](https://support.box.com).

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**. You're redirected to the Box Sign-on URL, where you can initiate the login flow.
- Go to Box Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Box tile in the My Apps, this option redirects to Box Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

### Push an Azure group to Box

You can push an Azure group to Box and sync that group. Azure pushes groups to Box via an API-level integration.

1. In **Users & Groups**, search for the group you want to assign to Box.
2. In **Provisioning**, ensure that **Synchronize Microsoft Entra groups to Box** is selected. This setting syncs the groups that you allocated in the preceding step. It might take some time for these groups to be pushed from Azure.

Note

If you need to create a user manually, contact [Box support team](https://support.box.com).

## Related content

Once you configure Box you can enforce Session Control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session Control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
