<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/moxtra-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Moxtra for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Moxtra with Microsoft Entra ID. When you integrate Moxtra with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Moxtra.
- Enable your users to be automatically signed-in to Moxtra with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Moxtra single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Moxtra supports **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Moxtra from the gallery

To configure the integration of Moxtra into Microsoft Entra ID, you need to add Moxtra from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Moxtra** in the search box.
4. Select **Moxtra** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Moxtra

Configure and test Microsoft Entra SSO with Moxtra using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Moxtra.

To configure and test Microsoft Entra SSO with Moxtra, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Moxtra SSO](#configure-moxtra-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Moxtra test user](#create-moxtra-test-user)** - to have a counterpart of B.Simon in Moxtra that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Moxtra** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following step:

   In the **Sign-on URL** text box, type the URL: `https://www.moxtra.com/service/#login`
6. Moxtra application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes. Select **Edit** icon to open User Attributes dialog.

   ![Screenshot shows the image of Moxtra application.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-attribute.png "Attributes")

7. In addition to above, Moxtra application expects few more attributes to be passed back in SAML response. In the User Claims section on the User Attributes dialog, perform the following steps to add SAML token attribute as shown in the below table:
   | Name | Source Attribute |
   | --- | --- |
   | firstname | user.givenname |
   | lastname | user.surname |
   | idpid | < Microsoft Entra Identifier > |


   Note


   The value of **idpid** attribute isn't real. You can get the actual value from **Set up Moxtra** section from step#8.


   1. Select **Add new claim** to open the **Manage user claims** dialog.
   2. In the **Name** textbox, type the attribute name shown for that row.
   3. Leave the **Namespace** blank.
   4. Select Source as **Attribute**.
   5. From the **Source attribute** list, type the attribute value shown for that row.
   6. Select **Ok**
   7. Select **Save**.

8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png "Certificate")

9. On the **Set up Moxtra** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration appropriate U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Moxtra SSO

1. In another browser window, sign on to your Moxtra company site as an administrator.
2. In the toolbar on the left, select **Admin Console > SAML Single Sign-on**, and then select **New**.

   ![Screenshot shows the S A M L Single Sign-on page with the option to create a new S A M L Single Sign-on.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/moxtra-tutorial/toolbar.png "Admin Console")

3. On the **SAML** page, perform the following steps:

   ![Screenshot shows the SAML page where you can enter the values described.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/moxtra-tutorial/admin.png "Administrator")


   a. In the **Name** textbox, type a name for your configuration \(such as **SAML**\).


   b. In the **IdP Entity ID** textbox, paste the value of **Microsoft Entra Identifier**..


   c. In **Login URL** textbox, paste the value of **Login URL**..


   d. In the **AuthnContextClassRef** textbox, type **urn:oasis:names:tc:SAML:2.0:ac:classes:Password**.


   e. In the **NameID Format** textbox, type **urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress**.


   f. Open certificate which you have downloaded from Azure portal in notepad, copy the content, and then paste it into the **Certificate** textbox.


   g. In the SAML email domain textbox, type your SAML email domain.


   Note


   To see the steps to verify the domain, select the "**i**" below.


   h. Select **Update**.

### Create Moxtra test user

The objective of this section is to create a user called B.simon in Moxtra.

**To create a user called B.simon in Moxtra, perform the following steps:**

1. Sign on to your Moxtra company site as an administrator.
2. In the toolbar on the left, select **Admin Console > User Management**, and then **Add User**.

   ![Screenshot shows the User Management page with Add User selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/moxtra-tutorial/user.png "Management")

3. On the **Add User** dialog, perform the following steps:

   a. In the **First Name** textbox, type **B**.

   b. In the **Last Name** textbox, type **Simon**.

   c. In the **Email** textbox, type B.simon's email address same as on Azure portal.

   d. In the **Division** textbox, type **Dev**.

   e. In the **Department** textbox, type **IT**.

   f. Select **Administrator**.

   g. Select **Add**.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Moxtra Sign-on URL where you can initiate the login flow.
- Go to Moxtra Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Moxtra tile in the My Apps, this option redirects to Moxtra Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Moxtra you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
