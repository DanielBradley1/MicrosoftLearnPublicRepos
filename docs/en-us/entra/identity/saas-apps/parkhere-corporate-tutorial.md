<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/parkhere-corporate-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure ParkHere Corporate for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate ParkHere Corporate with Microsoft Entra ID. When you integrate ParkHere Corporate with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to ParkHere Corporate.
- Enable your users to be automatically signed-in to ParkHere Corporate with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- ParkHere Corporate single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- ParkHere Corporate supports **IDP** initiated SSO.

## Add ParkHere Corporate from the gallery

To configure the integration of ParkHere Corporate into Microsoft Entra ID, you need to add ParkHere Corporate from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **ParkHere Corporate** in the search box.
4. Select **ParkHere Corporate** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for ParkHere Corporate

Configure and test Microsoft Entra SSO with ParkHere Corporate using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in ParkHere Corporate.

To configure and test Microsoft Entra SSO with ParkHere Corporate, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure ParkHere Corporate SSO](#configure-parkhere-corporate-sso)** - to configure the single sign-on settings on application side.

   1. **[Create ParkHere Corporate test user](#create-parkhere-corporate-test-user)** - to have a counterpart of B.Simon in ParkHere Corporate that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **ParkHere Corporate** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, the application is pre-configured and the necessary URLs are already pre-populated with Azure. The user needs to save the configuration by selecting the **Save** button.
6. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure ParkHere Corporate SSO

To configure single sign-on on **ParkHere Corporate** side, you need to send the **App Federation Metadata Url** to [ParkHere Corporate support team](mailto:support@park-here.eu). They set this setting to have the SAML SSO connection set properly on both sides.

### Create ParkHere Corporate test user

In this section, you create a user called Britta Simon in ParkHere Corporate. Work with [ParkHere Corporate support team](mailto:support@park-here.eu) to add the users in the ParkHere Corporate platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the ParkHere Corporate for which you set up the SSO.
- You can use Microsoft My Apps. When you select the ParkHere Corporate tile in the My Apps, you should be automatically signed in to the ParkHere Corporate for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure ParkHere Corporate you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
