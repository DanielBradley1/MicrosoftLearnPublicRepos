<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/checkproof-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure CheckProof for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate CheckProof with Microsoft Entra ID. When you integrate CheckProof with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to CheckProof.
- Enable your users to be automatically signed-in to CheckProof with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- CheckProof single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- CheckProof supports **IDP** initiated SSO.
- CheckProof supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/checkproof-provisioning-tutorial).

## Add CheckProof from the gallery

To configure the integration of CheckProof into Microsoft Entra ID, you need to add CheckProof from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **CheckProof** in the search box.
4. Select **CheckProof** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for CheckProof

Configure and test Microsoft Entra SSO with CheckProof using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in CheckProof.

To configure and test Microsoft Entra SSO with CheckProof, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure CheckProof SSO](#configure-checkproof-sso)** - to configure the single sign-on settings on application side.

   1. **[Create CheckProof test user](#create-checkproof-test-user)** - to have a counterpart of B.Simon in CheckProof that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **CheckProof** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Set up single sign-on with SAML** page, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://api.checkproof.com/api/v1/saml/<ID>/metadata`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://api.checkproof.com/api/v1/saml/<ID>/acs`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [CheckProof Client support team](mailto:support@checkproof.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up CheckProof** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure CheckProof SSO

1. In a different web browser window, sign into CheckProof website as an administrator.
2. Go to the **Settings > Company Settings > SAML SETTINGS** page and Upload the **Federation Metadata XML** in **Federation XML** textbox.

   ![SAML settings page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/checkproof-tutorial/settings.png)

### Create CheckProof test user

1. In a different web browser window, sign into CheckProof website as an administrator.
2. Select **Profile** and select **My profile**.

   ![CheckProof test user page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/checkproof-tutorial/create-user.png)

3. Select **CREATE USER**.
4. In the **CREATE USER** page, fill the required fields and select **SAVE**.

   ![CheckProof create user page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/checkproof-tutorial/user.png)

Note

CheckProof also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/checkproof-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the CheckProof for which you set up the SSO.
- You can use Microsoft My Apps. When you select the CheckProof tile in the My Apps, you should be automatically signed in to the CheckProof for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure CheckProof you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
