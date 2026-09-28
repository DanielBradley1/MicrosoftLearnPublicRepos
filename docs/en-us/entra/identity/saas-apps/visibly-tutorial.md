<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/visibly-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Visibly for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Visibly with Microsoft Entra ID. When you integrate Visibly with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Visibly.
- Enable your users to be automatically signed-in to Visibly with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Visibly single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Visibly supports **SP** initiated SSO.
- Visibly supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/visibly-provisioning-tutorial).

## Add Visibly from the gallery

To configure the integration of Visibly into Microsoft Entra ID, you need to add Visibly from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Visibly** in the search box.
4. Select **Visibly** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Visibly

Configure and test Microsoft Entra SSO with Visibly using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Visibly.

To configure and test Microsoft Entra SSO with Visibly, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Visibly SSO](#configure-visibly-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Visibly test user](#create-visibly-test-user)** - to have a counterpart of B.Simon in Visibly that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Visibly** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, enter the values for the following fields:

   a. In the **Sign-on URL** text box, type the URL: `https://app.visibly.io/`

   b. In the **Reply URL** text box, type the URL: `https://api.visibly.io/api/v1/verifyResponse`
6. Visibly application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

7. In addition to above, Visibly application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | city | user.city |
   | lastName | user.surname |
   | state | user.state |
   | department | user.department |
   | email | user.mail |
8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

9. On the **Set up Visibly** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Visibly SSO

1. Sign in to Visibly using your credentials.
2. Navigate to the **Settings** option from the navigation menu.

   ![Screenshot shows the settings option selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/visibly-tutorial/settings.png)

3. Select **Integrations** within Settings.

   ![Screenshot shows Integrations selected from the Settings menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/visibly-tutorial/integrations.png)

4. In the **Integrations**, select **SSO**.

   ![Screenshot shows S S O selected from the Integrations.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/visibly-tutorial/sso.png)

5. Perform the following steps in the following page.

   ![Screenshot shows S S O Integration page where you can enter the values described.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/visibly-tutorial/configuration.png)


   a. In the **Entity ID** textbox, paste the **Entity ID** value which you copied previously.


   b. In the **SSO url** textbox, paste the **Login URL** value which you copied previously.


   c. In the **SSO name** textbox, give any valid name.


   d. Open the downloaded **Certificate \(Base64\)** into Notepad and paste the content into the **Certificate** textbox or you can also upload the **Certificate** by selecting the **Upload Certificate**.


   e. Select **Save**.

### Create Visibly test user

In this section, a user called B.Simon is created in Visibly. Visibly supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Visibly, a new one is created after authentication.

Visibly also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/visibly-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application** in Azure portal. this option redirects to Visibly Sign-on URL where you can initiate the login flow.
- Go to Visibly Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Visibly tile in the My Apps, this option redirects to Visibly Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Visibly you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
