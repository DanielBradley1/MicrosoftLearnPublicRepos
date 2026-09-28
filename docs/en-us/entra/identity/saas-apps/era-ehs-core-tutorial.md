<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/era-ehs-core-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure ERA\_EHS\_CORE for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate ERA\_EHS\_CORE with Microsoft Entra ID. When you integrate ERA\_EHS\_CORE with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to ERA\_EHS\_CORE.
- Enable your users to be automatically signed-in to ERA\_EHS\_CORE with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- ERA\_EHS\_CORE single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- ERA\_EHS\_CORE supports **SP** initiated SSO.

## Add ERA\_EHS\_CORE from the gallery

To configure the integration of ERA\_EHS\_CORE into Microsoft Entra ID, you need to add ERA\_EHS\_CORE from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **ERA\_EHS\_CORE** in the search box.
4. Select **ERA\_EHS\_CORE** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for ERA\_EHS\_CORE

Configure and test Microsoft Entra SSO with ERA\_EHS\_CORE using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in ERA\_EHS\_CORE.

To configure and test Microsoft Entra SSO with ERA\_EHS\_CORE, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure ERA\_EHS\_CORE SSO](#configure-era_ehs_core-sso)** - to configure the single sign-on settings on application side.

   1. **[Create ERA\_EHS\_CORE test user](#create-era_ehs_core-test-user)** - to have a counterpart of B.Simon in ERA\_EHS\_CORE that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **ERA\_EHS\_CORE** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://www.era-env.com/era_ehs_core/<customername>`

   b. In the **Reply URL** text box, type a URL using one of the following patterns:

   | **Reply URL** |
   | --- |
   | `https://www.era-env.com/era_ehs_core/<customername>/home/externallogin` |
   | `https://www.era-env.com/era_ehs_core/saml2/spxflow/Acs` |


   c. In the **Sign on URL** text box, type a URL using the following pattern: `https://www.era-env.com/era_ehs_core/<customername>/home/externallogin`


   Note


   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [ERA\_EHS\_CORE Client support team](mailto:tech_support@era-ehs.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure ERA\_EHS\_CORE SSO

To configure single sign-on on **ERA\_EHS\_CORE** side, you need to send the **App Federation Metadata Url** to [ERA\_EHS\_CORE support team](mailto:tech_support@era-ehs.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create ERA\_EHS\_CORE test user

In this section, you create a user called Britta Simon at ERA\_EHS\_CORE. Work with [ERA\_EHS\_CORE support team](mailto:tech_support@era-ehs.com) to add the users in the ERA\_EHS\_CORE platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to ERA\_EHS\_CORE Sign-on URL where you can initiate the login flow.
- Go to ERA\_EHS\_CORE Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the ERA\_EHS\_CORE tile in the My Apps, this option redirects to ERA\_EHS\_CORE Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure ERA\_EHS\_CORE you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
