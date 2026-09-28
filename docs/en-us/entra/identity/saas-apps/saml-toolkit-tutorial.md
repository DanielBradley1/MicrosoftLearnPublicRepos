<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/saml-toolkit-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Microsoft Entra SAML Toolkit for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Microsoft Entra SAML Toolkit with Microsoft Entra ID. When you integrate Microsoft Entra SAML Toolkit with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Microsoft Entra SAML Toolkit.
- Enable your users to be automatically signed-in to Microsoft Entra SAML Toolkit with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Microsoft Entra SAML Toolkit single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Microsoft Entra SAML Toolkit supports **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Microsoft Entra SAML Toolkit from the gallery

To configure the integration of Microsoft Entra SAML Toolkit into Microsoft Entra ID, you need to add Microsoft Entra SAML Toolkit from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Microsoft Entra SAML Toolkit** in the search box.
4. Select **Microsoft Entra SAML Toolkit** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Microsoft Entra SAML Toolkit

Configure and test Microsoft Entra SSO with Microsoft Entra SAML Toolkit using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Microsoft Entra SAML Toolkit.

To configure and test Microsoft Entra SSO with Microsoft Entra SAML Toolkit, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   - **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   - **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Microsoft Entra SAML Toolkit SSO](#configure-azure-ad-saml-toolkit-sso)** - to configure the single sign-on settings on application side.

   - **[Create Microsoft Entra SAML Toolkit test user](#create-azure-ad-saml-toolkit-test-user)** - to have a counterpart of B.Simon in Microsoft Entra SAML Toolkit that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Microsoft Entra SAML Toolkit** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Reply URL** text box, type the URL: `https://samltoolkit.azurewebsites.net/SAML/Consume`

   b. In the **Sign on URL** text box, type the URL: `https://samltoolkit.azurewebsites.net/`
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Raw\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificateraw.png)

7. On the **Set up Microsoft Entra SAML Toolkit** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Microsoft Entra SAML Toolkit SSO

1. Open a new web browser window, if you have not registered in the Microsoft Entra SAML Toolkit website, first register by selecting the **Register**. If you have registered already, sign into your Microsoft Entra SAML Toolkit company site using the registered sign-in credentials.

   ![Microsoft Entra SAML Toolkit Register](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/saml-toolkit-tutorial/register.png)

2. In the **SAML Toolkit** window, select **SAML Configuration**.
3. Select **Create**.

   ![Microsoft Entra SAML Toolkit](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/saml-toolkit-tutorial/createsso.png)

4. On the **SAML SSO Configuration** page, perform the following steps:

   ![Microsoft Entra SAML Toolkit Create SSO Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/saml-toolkit-tutorial/fill-details.png)


   1. In the **Login URL** textbox, paste the **Login URL** value, which you copied previously.
   2. In the **Microsoft Entra Identifier** textbox, paste the **Microsoft Entra Identifier** value, which you copied previously.
   3. In the **Logout URL** textbox, paste the **Logout URL** value, which you copied previously.
   4. Select **Choose File** and upload the **Certificate \(Raw\)** file which you have downloaded.
   5. Select **Create**.
   6. Copy Sign-on URL, Identifier and ACS URL values on SAML Toolkit SSO configuration page and paste into respected textboxes in the **Basic SAML Configuration section**.

### Create Microsoft Entra SAML Toolkit test user

In this section, a user called B.Simon is created in Microsoft Entra SAML Toolkit. Please create a test user in the tool by registering a new user and provide all the user details.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Microsoft Entra SAML Toolkit Sign-on URL where you can initiate the login flow.
- Go to Microsoft Entra SAML Toolkit Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Microsoft Entra SAML Toolkit tile in the My Apps, this option redirects to Microsoft Entra SAML Toolkit Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Microsoft Entra SAML Toolkit you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
