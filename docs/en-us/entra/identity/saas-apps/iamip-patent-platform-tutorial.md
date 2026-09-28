<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/iamip-patent-platform-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure IamIP Platform for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate IamIP Platform with Microsoft Entra ID. When you integrate IamIP Platform with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to IamIP Platform.
- Enable your users to be automatically signed-in to IamIP Platform with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- An IamIP Platform subscription with single sign-on \(SSO\) enabled.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- IamIP Platform supports SP-initiated and IDP-initiated SSO.
- IamIP Platform supports **Just In Time** user provisioning.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add IamIP Platform from the gallery

To configure the integration of IamIP Platform into Microsoft Entra ID, you need to add IamIP Platform from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **IamIP Platform** in the search box.
4. Select **IamIP Platform** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for IamIP Platform

Configure and test Microsoft Entra SSO with IamIP Platform using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in IamIP Platform.

To configure and test Microsoft Entra SSO with IamIP Platform, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure IamIP Platform SSO](#configure-iamip-platform-sso)** - to configure the single sign-on settings on application side.

   1. **[Create IamIP Platform test user](#create-iamip-platform-test-user)** - to have a counterpart of B.Simon in IamIP Platform that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **IamIP Platform** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, the user doesn't have to perform any step as the app is already pre-integrated with Azure.
6. On the **Basic SAML Configuration** section, if you wish to configure the application in **SP** initiated mode, perform the following steps:

   a. In the **Identifier** textbox, type the URL: `https://accounts.iamip.com/`

   b. In the **Reply URL** text box, type one of the following URLs:

   | **Reply URL** |
   | --- |
   | `https://accounts.iamip.com/sso-callback` |
   | `https://accounts.iamip.com/sso-login` |
   | `https://accounts.iamip.com/sso-logout` |


   c. In the **Sign-on URL** text box, type one of the following URLs:


   | **Sign-on URL** |
   | --- |
   | `https://accounts.iamip.com/login` |
   | `https://patents.iamip.com/login-user` |

7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

8. On the **Set up IamIP Platform** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure IamIP Platform SSO

To configure single sign-on on **IamIP Platform** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [IamIP Platform support team](mailto:info@iamip.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create IamIP Platform test user

In this section, a user called Britta Simon is created in IamIP Platform. IamIP Platform supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in IamIP Platform, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to IamIP Platform Sign on URL where you can initiate the login flow.
- Go to IamIP Platform Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the IamIP Platform for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the IamIP Platform tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the IamIP Platform for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure IamIP Platform you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
