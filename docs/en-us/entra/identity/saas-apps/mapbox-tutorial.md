<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/mapbox-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Mapbox for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Mapbox with Microsoft Entra ID. When you integrate Mapbox with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Mapbox.
- Enable your users to be automatically signed-in to Mapbox with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Mapbox single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Mapbox supports **IDP** initiated SSO

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Adding Mapbox from the gallery

To configure the integration of Mapbox into Microsoft Entra ID, you need to add Mapbox from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Mapbox** in the search box.
4. Select **Mapbox** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Mapbox

Configure and test Microsoft Entra SSO with Mapbox using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Mapbox.

To configure and test Microsoft Entra SSO with Mapbox, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Mapbox SSO](#configure-mapbox-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Mapbox test user](#create-mapbox-test-user)** - to have a counterpart of B.Simon in Mapbox that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Mapbox** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, the application is pre-configured and the necessary URLs are already pre-populated with Azure. The user needs to save the configuration by selecting the **Save** button.
6. Mapbox application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

7. In addition to above, Mapbox application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | role | user.assignedroles |
   |  |  |


   Note


   To understand how to configure roles in Microsoft Entra ID, see [here](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#app-roles-ui).

8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Raw\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificateraw.png)

9. On the **Set up Mapbox** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Mapbox SSO

1. In a different web browser window, sign into Mapbox as an administrator.
2. Select the **Settings** tab.

   ![Mapbox Settings tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mapbox-tutorial/configure1.png)

3. Select the **Security** tab from the left navigation pane.

   ![Mapbox Security tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mapbox-tutorial/configure2.png)

4. Select **Edit single sign-on**.

   ![Mapbox Edit single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mapbox-tutorial/configure3.png)

5. Scroll down to **Step 3: Setup SAML single sign-on for Mapbox** and perform the following steps:

   ![Mapbox Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/mapbox-tutorial/configure4.png)


   1. In the **Idp Sign-on URL** textbox, paste **Login URL** value, which you copied previously.
   2. In the **Issuer ID** textbox, paste **Microsoft Entra Identifier** value, which you copied previously.
   3. Open the downloaded **Certificate \(Raw\)** file into Notepad and copy content of certificate file and paste it into the **X.509 certificate** textbox.
   4. Select **Save single sign-on settings**.

### Create Mapbox test user

In this section, you create a user called Britta Simon in Mapbox. Work with [Mapbox support team](mailto:help@mapbox.com) to add the users in the Mapbox platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the Mapbox for which you set up the SSO
- You can use Microsoft My Apps. When you select the Mapbox tile in the My Apps, you should be automatically signed in to the Mapbox for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Mapbox you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
