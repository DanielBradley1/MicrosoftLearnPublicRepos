<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/lcvista-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure LCVista for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate LCVista with Microsoft Entra ID. When you integrate LCVista with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to LCVista.
- Enable your users to be automatically signed-in to LCVista with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To configure Microsoft Entra integration with LCVista, you need the following items:

- A Microsoft Entra subscription. If you don't have a Microsoft Entra environment, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- LCVista single sign-on enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- LCVista supports **SP** initiated SSO.

## Add LCVista from the gallery

To configure the integration of LCVista into Microsoft Entra ID, you need to add LCVista from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **LCVista** in the search box.
4. Select **LCVista** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for LCVista

Configure and test Microsoft Entra SSO with LCVista using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in LCVista.

To configure and test Microsoft Entra SSO with LCVista, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure LCVista SSO](#configure-lcvista-sso)** - to configure the single sign-on settings on application side.

   1. **[Create LCVista test user](#create-lcvista-test-user)** - to have a counterpart of B.Simon in LCVista that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **LCVista** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://<subdomain>.lcvista.com`

   b. In the **Sign on URL** text box, type a URL using the following pattern: `https://<subdomain>.lcvista.com/rainier/login`

   Note

   These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [LCVista Client support team](https://lcvista.com/contact) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up LCVista** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure LCVista SSO

1. Log into your LCVista application as an administrator.
2. In the **SAML Config** section, check the **Enable SAML login** and enter the details as mentioned in below image.

   ![Configure Single Sign-On](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/lcvista-tutorial/configuration.png)


   a. In the **Entity ID** textbox, paste **Microsoft Entra Identifier** value, which you copied previously.


   b. In the **URL** textbox, paste **Login URL** value, which you copied previously.


   c. Open the Metadata XML file which you have downloaded from Azure portal into Notepad, copy the value **X509Certificate** and paste it in the **x509 Certificate** section.


   d. In the **First name attribute** textbox, paste the value `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname`.


   e. In the **Last name attribute** textbox, paste the value `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/surname`.


   f. In the **Email attribute** textbox, paste the value `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress`.


   g. In the **Username attribute** textbox, paste the value `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`.


   e. Select **Save** to save the settings.

### Create LCVista test user

In this section, you create a user called Britta Simon in LCVista. Work with [LCVista Client support team](https://lcvista.com/contact) to add the users in the LCVista platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to LCVista Sign-on URL where you can initiate the login flow.
- Go to LCVista Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the LCVista tile in the My Apps, this option redirects to LCVista Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure LCVista you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
