<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/planview-leankit-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Planview LeanKit for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Planview LeanKit with Microsoft Entra ID. When you integrate Planview LeanKit with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Planview LeanKit.
- Enable your users to be automatically signed-in to Planview LeanKit with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Planview LeanKit single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Planview LeanKit supports **SP** and **IDP** initiated SSO.

## Add Planview LeanKit from the gallery

To configure the integration of Planview LeanKit into Microsoft Entra ID, you need to add Planview LeanKit from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Planview LeanKit** in the search box.
4. Select **Planview LeanKit** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Planview LeanKit

Configure and test Microsoft Entra SSO with Planview LeanKit using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Planview LeanKit.

To configure and test Microsoft Entra SSO with Planview LeanKit, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Planview LeanKit SSO](#configure-planview-leankit-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Planview LeanKit test user](#create-planview-leankit-test-user)** - to have a counterpart of B.Simon in Planview LeanKit that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Planview LeanKit** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type a URL using the following pattern: `https://<HostName>.leankit.com`

   b. In the **Reply URL** textbox, type a URL using the following pattern: `https://<HostName>.leankit.com/Account/Membership/ExternalLogin`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign on URL** text box, type a URL using the following pattern: `https://<HostName>.leankit.com/login`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [Planview LeanKit support team](mailto:support@leankit.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png "Certificate")

8. On the **Set up Planview LeanKit** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration appropriate U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Attributes")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Planview LeanKit SSO

To configure single sign-on on **Planview LeanKit** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Planview LeanKit support team](mailto:support@leankit.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Planview LeanKit test user

In this section, you create a user called Britta Simon in Planview LeanKit. Work with [Planview LeanKit support team](mailto:support@leankit.com) to add the users in the Planview LeanKit platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Planview LeanKit Sign on URL where you can initiate the login flow.
- Go to Planview LeanKit Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Planview LeanKit for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Planview LeanKit tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Planview LeanKit for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Planview LeanKit you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
