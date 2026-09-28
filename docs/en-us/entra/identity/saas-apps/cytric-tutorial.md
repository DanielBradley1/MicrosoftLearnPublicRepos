<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/cytric-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Cytric for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Cytric with Microsoft Entra ID. When you integrate Cytric with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Cytric.
- Enable your users to be automatically signed-in to Cytric with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Cytric single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Cytric supports **SP** initiated SSO.

## Add Cytric from the gallery

To configure the integration of Cytric into Microsoft Entra ID, you need to add Cytric from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Cytric** in the search box.
4. Select **Cytric** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Cytric

Configure and test Microsoft Entra SSO with Cytric using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Cytric.

To configure and test Microsoft Entra SSO with Cytric, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Cytric SSO](#configure-cytric-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Cytric test user](#create-cytric-test-user)** - to have a counterpart of B.Simon in Cytric that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Cytric** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type a URL using the following pattern: `https://<domain>.cytric.net/saml2`

   b. In the **Reply URL** textbox, type a URL using the following pattern: `https://<domain>.cytric.net/saml2/sp/acs/post`

   c. In the **Sign on URL** text box, type a URL using the following pattern: `https://<domain>.cytric.net/svc/SAML2/cWS/pre/AUTH?clientId=<Customer>`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [Cytric support team](mailto:ifao.cgs@amadeus.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

7. On the **Set up Cytric** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration appropriate URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Attributes")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Cytric SSO

To configure single sign-on on **Cytric** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Cytric support team](mailto:ifao.cgs@amadeus.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Cytric test user

In this section, you create a user called Britta Simon in Cytric. Work with [Cytric support team](mailto:ifao.cgs@amadeus.com) to add the users in the Cytric platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Cytric Sign-on URL where you can initiate the login flow.
- Go to Cytric Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Cytric tile in the My Apps, this option redirects to Cytric Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Cytric you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
