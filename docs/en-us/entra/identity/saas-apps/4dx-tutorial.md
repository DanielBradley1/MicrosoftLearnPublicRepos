<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/4dx-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure 4DX for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate 4DX with Microsoft Entra ID. When you integrate 4DX with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to 4DX.
- Enable your users to be automatically signed-in to 4DX with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- 4DX single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- 4DX supports **IDP** initiated SSO.

## Add 4DX from the gallery

To configure the integration of 4DX into Microsoft Entra ID, you need to add 4DX from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **4DX** in the search box.
4. Select **4DX** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for 4DX

Configure and test Microsoft Entra SSO with 4DX using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in 4DX.

To configure and test Microsoft Entra SSO with 4DX, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure 4DX SSO](#configure-4dx-sso)** - to configure the single sign-on settings on application side.

   1. **[Create 4DX test user](#create-4dx-test-user)** - to have a counterpart of B.Simon in 4DX that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **4DX** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, the application is pre-configured and the necessary URLs are already pre-populated with Azure. The user needs to save the configuration by selecting the **Save** button.
6. 4DX application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Image")

7. In addition to above, 4DX application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | companykey | `<unique ID>` |


   Note


   For this `<unique ID>` of a customer assertion, please reach out to [4DX support team](mailto:support@bahrcode.com).

8. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

9. On the **Set up 4DX** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows how to copy a configuration appropriate URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Attributes")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure 4DX SSO

To configure single sign-on on **4DX** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [4DX support team](mailto:support@bahrcode.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create 4DX test user

In this section, you create a user called Britta Simon in 4DX. Work with [4DX support team](mailto:support@bahrcode.com) to add the users in the 4DX platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- select **Test this application**, and you should be automatically signed in to the 4DX for which you set up the SSO.
- You can use Microsoft My Apps. When you select the 4DX tile in the My Apps, you should be automatically signed in to the 4DX for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure 4DX you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
