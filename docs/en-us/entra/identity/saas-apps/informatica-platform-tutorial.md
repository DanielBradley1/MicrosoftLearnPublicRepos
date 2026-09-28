<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/informatica-platform-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Informatica Platform for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Informatica Platform with Microsoft Entra ID. When you integrate Informatica Platform with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Informatica Platform.
- Enable your users to be automatically signed-in to Informatica Platform with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Informatica Platform single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Informatica Platform supports **SP** and **IDP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Informatica Platform from the gallery

To configure the integration of Informatica Platform into Microsoft Entra ID, you need to add Informatica Platform from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Informatica Platform** in the search box.
4. Select **Informatica Platform** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Informatica Platform

Configure and test Microsoft Entra SSO with Informatica Platform using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Informatica Platform.

To configure and test Microsoft Entra SSO with Informatica Platform, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Informatica Platform SSO](#configure-informatica-platform-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Informatica Platform test user](#create-informatica-platform-test-user)** - to have a counterpart of B.Simon in Informatica Platform that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Informatica Platform** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type the following value or URL pattern:

   | App | URL |
   | --- | --- |
   | For EDC | `Informatica` |
   | For Axon | `https://<host name: port number>/saml/metadata` |


   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<host name: port number>/administrator/Login.do`

6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://<host name: port number>/administrator/saml/login`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-on URL. Contact [Informatica Platform Client support team](mailto:support@informatica.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. Informatica Platform application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

8. In addition to above, Informatica Platform application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | firstName | user.givenname |
   | lastName | user.surname |
   | email | user.mail |
   | Administrator | user.givenname |
9. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(PEM\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificate-base64-download.png)

10. On the **Set up Informatica Platform** section, copy the appropriate URL\(s\) based on your requirement.

    ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Informatica Platform SSO

To configure single sign-on on **Informatica Platform** side, you need to send the downloaded **Certificate \(PEM\)** and appropriate copied URLs from the application configuration to [Informatica Platform support team](mailto:support@informatica.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Informatica Platform test user

In this section, you create a user called Britta Simon in Informatica Platform. Work with [Informatica Platform support team](mailto:support@informatica.com) to add the users in the Informatica Platform platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Informatica Platform Sign on URL where you can initiate the login flow.
- Go to Informatica Platform Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Informatica Platform for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Informatica Platform tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Informatica Platform for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Informatica Platform you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
