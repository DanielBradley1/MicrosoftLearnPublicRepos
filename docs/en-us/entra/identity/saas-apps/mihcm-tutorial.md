<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/mihcm-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure MiHCM for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate MiHCM with Microsoft Entra ID. When you integrate MiHCM with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to MiHCM.
- Enable your users to be automatically signed-in to MiHCM with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- MiHCM single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- MiHCM supports **SP** initiated SSO.

## Add MiHCM from the gallery

To configure the integration of MiHCM into Microsoft Entra ID, you need to add MiHCM from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **MiHCM** in the search box.
4. Select **MiHCM** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for MiHCM

Configure and test Microsoft Entra SSO with MiHCM using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in MiHCM.

To configure and test Microsoft Entra SSO with MiHCM, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure MiHCM SSO](#configure-mihcm-sso)** - to configure the single sign-on settings on application side.

   1. **[Create MiHCM test user](#create-mihcm-test-user)** - to have a counterpart of B.Simon in MiHCM that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **MiHCM** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** box, type a URL using the following pattern: `https://<subdomain>.mihcm.com`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://login.mihcm.com/<subdomain>/Acs`

   c. In the **Sign-on URL** text box, type a URL using the following pattern: `https://<subdomain>.mihcm.com`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [MiHCM Client support team](mailto:support@mihcm.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure MiHCM SSO

To configure single sign-on on **MiHCM** side, you need to send the **App Federation Metadata Url** to [MiHCM support team](mailto:support@mihcm.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create MiHCM test user

In this section, you create a user called Britta Simon in MiHCM. Work with [MiHCM support team](mailto:support@mihcm.com) to add the users in the MiHCM platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to MiHCM Sign-on URL where you can initiate the login flow.
- Go to MiHCM Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the MiHCM tile in the My Apps, this option redirects to MiHCM Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure MiHCM you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
