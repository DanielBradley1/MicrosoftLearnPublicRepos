<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/sketch-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Sketch for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Sketch with Microsoft Entra ID. When you integrate Sketch with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Sketch.
- Enable your users to be automatically signed-in to Sketch with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Sketch single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Sketch supports **SP** initiated SSO.
- Sketch supports **Just In Time** user provisioning.

## Add Sketch from the gallery

To configure the integration of Sketch into Microsoft Entra ID, you need to add Sketch from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Sketch** in the search box.
4. Select **Sketch** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Sketch

Configure and test Microsoft Entra SSO with Sketch using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Sketch.

To configure and test Microsoft Entra SSO with Sketch, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Sketch SSO](#configure-sketch-sso)** - to configure the single sign-on settings on application side.
3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Choose a shortname for your Workspace in Sketch

Follow these steps to choose a shortname and gather information to continue the setup process in Microsoft Entra ID.

Note

Before starting this process, make sure SSO is available in your Workspace, check there is an SSO tab in your Workspace Admin panel. If you don't see the SSO tab, please reach out to customer support.

1. [Sign in to your Workspace](https://www.sketch.com/signin/) as an Admin.
2. Head to the **People & Settings** section in the sidebar.
3. Select the **Single Sign-On** tab.
4. Select **Choose** a short name.
5. Enter a unique name, it should have less than 16 characters and can only include letters, numbers or hyphens. You can edit this name later on.
6. Select **Submit**.
7. Select the first tab **Set Up Identity Provider**. In this tab, you’ll find the unique Workspace values you’ll need to set up the integration with Microsoft Entra ID.

   1. **EntityID:** In Microsoft Entra ID, this is the `Identifier` field.
   2. **ACS URL:** In Microsoft Entra ID, this is the `Reply URL` field.

Make sure to keep these values at hand! You’ll need them in the next step. Select Copy next to each value to copy it to your clipboard.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Sketch** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, use the `EntityID` field from the previous step. It looks like: `sketch-<uuid_v4>`

   b. In the **Reply URL** textbox, use the `ACS URL` field from the previous step. It looks like: `https://sso.sketch.com/saml/acs?id=<uuid_v4>`
6. Select **Set additional URLs** and perform the following step:

   In the **Sign-on URL** text box, type the URL: `https://www.sketch.com`

   Note

   Please use **Identifier** and **Reply URL** values from [Choose a shortname for your Workspace in Sketch](#choose-a-shortname-for-your-workspace-in-sketch) section.
7. Sketch application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attribute mappings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Attributes")

8. In addition to above, Sketch application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | email | user.mail |
   | first\_name | user.givenname |
   | surname | user.surname |
9. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Sketch SSO

Follow these steps to finish the configuration in Sketch.

1. In your Workspace, head to the **Set up Sketch** tab in the **Single Sign-On** window.
2. Upload the XML file you downloaded previously in the **Import XML Metadata file** section.
3. Log out.
4. Select **Sign in with SSO**.
5. Use the shortname you configured previously to proceed.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Sketch Sign-on URL where you can initiate the login flow.
- Go to Sketch Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Sketch tile in the My Apps, this option redirects to Sketch Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Sketch you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
