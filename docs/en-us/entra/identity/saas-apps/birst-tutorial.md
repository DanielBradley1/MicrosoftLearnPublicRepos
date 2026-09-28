<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/birst-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Birst Agile Business Analytics for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Birst Agile Business Analytics with Microsoft Entra ID. When you integrate Birst Agile Business Analytics with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Birst Agile Business Analytics.
- Enable your users to be automatically signed-in to Birst Agile Business Analytics with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Birst Agile Business Analytics single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Birst Agile Business Analytics supports **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Birst Agile Business Analytics from the gallery

To configure the integration of Birst Agile Business Analytics into Microsoft Entra ID, you need to add Birst Agile Business Analytics from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Birst Agile Business Analytics** in the search box.
4. Select **Birst Agile Business Analytics** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Birst Agile Business Analytics

Configure and test Microsoft Entra SSO with Birst Agile Business Analytics using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Birst Agile Business Analytics.

To configure and test Microsoft Entra SSO with Birst Agile Business Analytics, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Birst Agile Business Analytics SSO](#configure-birst-agile-business-analytics-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Birst Agile Business Analytics test user](#create-birst-agile-business-analytics-test-user)** - to have a counterpart of B.Simon in Birst Agile Business Analytics that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Birst Agile Business Analytics** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   In the **Sign-on URL** textbox, type a URL using the following pattern: `https://login.bws.birst.com/SAMLSSO/Services.aspx?birst.idpid=<TENANTIDPID>`

   The URL depends on the datacenter that your Birst account is located:

   - For US datacenter use following the pattern: `https://login.bws.birst.com/SAMLSSO/Services.aspx?birst.idpid=<TENANTIDPID>`
   - For Europe datacenter use the following pattern: `https://login.eu1.birst.com/SAMLSSO/Services.aspx?birst.idpid=<TENANTIDPID>`

     Note

     This value isn't real. Update the value with the actual Sign-On URL. Contact [Birst Agile Business Analytics Client support team](mailto:info@birst.com) to get the value.

6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png "Certificate")

7. On the **Set up Birst Agile Business Analytics** section, copy the appropriate URL\(s\) as per your requirement.

   ![Screenshot shows to copy configuration appropriate U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Birst Agile Business Analytics SSO

To configure single sign-on on **Birst Agile Business Analytics** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Birst Agile Business Analytics support team](mailto:info@birst.com). They set this setting to have the SAML SSO connection set properly on both sides.

Note

Mention to Birst team that this integration needs SHA256 Algorithm \(SHA1 isn't supported\) so that they can set the SSO on the appropriate server like **app2101** , and so on.

### Create Birst Agile Business Analytics test user

In this section, you create a user called Britta Simon in Birst Agile Business Analytics. Work with [Birst Agile Business Analytics support team](mailto:info@birst.com) to add the users in the Birst Agile Business Analytics platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Birst Agile Business Analytics Sign-on URL where you can initiate the login flow.
- Go to Birst Agile Business Analytics Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Birst Agile Business Analytics tile in the My Apps, this option redirects to Birst Agile Business Analytics Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Birst Agile Business Analytics you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
