<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/flexera-one-tutorial -->
<!-- Sitemap-Last-Modified: 2026-05-26 -->

# Configure Flexera One for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Flexera One with Microsoft Entra ID. When you integrate Flexera One with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Flexera One.
- Enable your users to be automatically signed-in to Flexera One with their Microsoft Entra accounts.
- Manage your accounts in one central location.

Flexera One is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Flexera One single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Flexera One supports **SP and IDP** initiated SSO.
- Flexera One supports **Just In Time** user provisioning.

## Add Flexera One from the gallery

To configure the integration of Flexera One into Microsoft Entra ID, you need to add Flexera One from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Flexera One** in the search box.
4. Select **Flexera One** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Flexera One

Configure and test Microsoft Entra SSO with Flexera One using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Flexera One.

To configure and test Microsoft Entra SSO with Flexera One, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Flexera One SSO](#configure-flexera-one-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Flexera One test user](#create-flexera-one-test-user)** - to have a counterpart of B.Simon in Flexera One that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Flexera One** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://secure.flexera.com/sso/saml2/<ID>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://secure.flexera.com/sso/saml2/<ID>`

   c. In the **Sign-on URL** text box, type a URL using the following pattern: `https://secure.flexera.com/sso/saml2/<ID>`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-on URL. Contact [Flexera One Client support team](mailto:support@flexera.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. Flexera One application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of Flexera One application.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Attributes")

7. In addition to above, Flexera One application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | firstName | user.givenname |
   | lastName | user.surname |
8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png "Certificate")

9. On the **Set up Flexera One** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy Configuration appropriate U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Configuration")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Flexera One SSO

To configure single sign-on on **Flexera One** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Flexera One support team](mailto:support@flexera.com). They set this setting to have the SAML SSO connection set properly on both sides. Learn [how](https://docs.flexera.com/flexera/EN/Administration/AzureADSSO.htm).

### Create Flexera One test user

In this section, a user called Britta Simon is created in Flexera One. Flexera One supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Flexera One, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Flexera One Sign on URL where you can initiate the login flow.
- Go to Flexera One Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Flexera One for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Flexera One tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Flexera One for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Flexera One you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
