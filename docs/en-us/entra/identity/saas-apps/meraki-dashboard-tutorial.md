<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/meraki-dashboard-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Meraki Dashboard for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Meraki Dashboard with Microsoft Entra ID. When you integrate Meraki Dashboard with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Meraki Dashboard.
- Enable your users to be automatically signed-in to Meraki Dashboard with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Meraki Dashboard single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Meraki Dashboard supports **IDP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Adding Meraki Dashboard from the gallery

To configure the integration of Meraki Dashboard into Microsoft Entra ID, you need to add Meraki Dashboard from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Meraki Dashboard** in the search box.
4. Select **Meraki Dashboard** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Meraki Dashboard

Configure and test Microsoft Entra SSO with Meraki Dashboard using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Meraki Dashboard.

To configure and test Microsoft Entra SSO with Meraki Dashboard, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Meraki Dashboard SSO](#configure-meraki-dashboard-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Meraki Dashboard Admin Roles](#create-meraki-dashboard-admin-roles)** - to have a counterpart of B.Simon in Meraki Dashboard that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Meraki Dashboard** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the edit/pen icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   In the **Reply URL** textbox, type a URL using the following pattern: `https://n27.meraki.com/saml/login/m9ZEgb/< UNIQUE ID >`

   Note

   The Reply URL value isn't real. Update this value with the actual Reply URL value, which is explained later in the article.
6. Select the **Save** button.
7. Meraki Dashboard application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

8. In addition to above, Meraki Dashboard application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | `https://dashboard.meraki.com/saml/attributes/username` | user.userprincipalname |
   | `https://dashboard.meraki.com/saml/attributes/role` | user.assignedroles |


   Note


   To understand how to configure roles in Microsoft Entra ID, see [here](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#app-roles-ui).

9. In the **SAML Signing Certificate** section, select **Edit** button to open **SAML Signing Certificate** dialog.

   ![Edit SAML Signing Certificate](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-certificate.png)

10. In the **SAML Signing Certificate** section, copy the **Thumbprint Value** and save it on your computer. This value needs to be converted to include colons in order for the Meraki dashboard to understand it . For example, if the thumbprint from Azure is `C2569F50A4AAEDBB8E` it will need to be changed to `C2:56:9F:50:A4:AA:ED:BB:8E` to use it later in Meraki Dashboard.

    ![Copy Thumbprint value](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-thumbprint.png)

11. On the **Set up Meraki Dashboard** section, copy the Logout URL value and save it on your computer.

    ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Meraki Dashboard SSO

1. In a different web browser window, sign in to your Meraki Dashboard company site as an administrator
2. Navigate to **Organization** > **Settings**.

   ![Meraki Dashboard Settings tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meraki-dashboard-tutorial/configure-1.png)

3. Under Authentication, change **SAML SSO** to **SAML SSO enabled**.

   ![Meraki Dashboard Authentication](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meraki-dashboard-tutorial/configure-2.png)

4. Select **Add a SAML IdP**.

   ![Meraki Dashboard Add a SAML IdP](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meraki-dashboard-tutorial/configure-3.png)

5. Paste the converted **Thumbprint** Value, which you have copied and converted in specified format as mentioned in step 9 of previous section into **X.590 cert SHA1 fingerprint** textbox. Then select **Save**. After saving, the Consumer URL will show up. Copy Consumer URL value and paste this into **Reply URL** textbox in the **Basic SAML Configuration Section**.

   ![Meraki Dashboard Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meraki-dashboard-tutorial/configure-4.png)

### Create Meraki Dashboard Admin Roles

1. In a different web browser window, sign into meraki dashboard as an administrator.
2. Navigate to **Organization** > **Administrators**.

   ![Meraki Dashboard Administrators](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meraki-dashboard-tutorial/user-1.png)

3. In the SAML administrator roles section, select the **Add SAML role** button.

   ![Meraki Dashboard Add SAML role button](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meraki-dashboard-tutorial/user-2.png)

4. Enter the Role **meraki\_full\_admin**, mark **Organization access** as **Full** and select **Create role**. Repeat the process for **meraki\_readonly\_admin**, this time mark **Organization access** as **Read-only** box.

   ![Meraki Dashboard create user](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meraki-dashboard-tutorial/user-3.png)

5. Follow the below steps to map the Meraki Dashboard roles to Microsoft Entra SAML roles:

   ![Screenshot for App roles.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/meraki-dashboard-tutorial/app-role.png)


   a. In the Azure portal, select **App Registrations**.


   b. Select All Applications and select **Meraki Dashboard**.


   c. Select **App Roles** and select **Create App role**.


   d. Enter the Display name as `Meraki Full Admin`.


   e. Select Allowed Members as `Users/Groups`.


   f. Enter the Value as `meraki_full_admin`.


   g. Enter the Description as `Meraki Full Admin`.


   h. Select **Save**.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the Meraki Dashboard for which you set up the SSO
- You can use Microsoft My Apps. When you select the Meraki Dashboard tile in the My Apps, you should be automatically signed in to the Meraki Dashboard for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Meraki Dashboard you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
