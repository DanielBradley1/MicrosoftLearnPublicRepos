<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/cic-intelligent-compensation-control-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure CIC - Controle Inteligente de Compensação for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate CIC - Controle Inteligente de Compensação with Microsoft Entra ID. When you integrate CIC - Controle Inteligente de Compensação with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to CIC - Controle Inteligente de Compensação.
- Enable your users to be automatically signed-in to CIC - Controle Inteligente de Compensação with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- CIC - Controle Inteligente de Compensação single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- CIC - Controle Inteligente de Compensação supports **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add CIC - Controle Inteligente de Compensação from the gallery

To configure the integration of CIC - Controle Inteligente de Compensação into Microsoft Entra ID, you need to add CIC - Controle Inteligente de Compensação from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **CIC - Controle Inteligente de Compensação** in the search box.
4. Select **CIC - Controle Inteligente de Compensação** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for CIC - Controle Inteligente de Compensação

Configure and test Microsoft Entra SSO with CIC - Controle Inteligente de Compensação using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in CIC - Controle Inteligente de Compensação.

To configure and test Microsoft Entra SSO with CIC - Controle Inteligente de Compensação, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure CIC - Controle Inteligente de Compensação SSO](#configure-cic---controle-inteligente-de-compensa%C3%A7%C3%A3o-sso)** - to configure the single sign-on settings on application side.

   1. **[Create CIC - Controle Inteligente de Compensação test user](#create-cic---controle-inteligente-de-compensa%C3%A7%C3%A3o-test-user)** - to have a counterpart of B.Simon in CIC - Controle Inteligente de Compensação that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **CIC - Controle Inteligente de Compensação** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type the value: `cic-prod`

   b. In the **Reply URL** text box, type the URL: `https://prodgtw.perdcomp.com.br/auth/login/saml/callback`

   c. In the **Sign on URL** text box, type the URL: `https://perdcomp.com.br/`
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

7. On the **Set up CIC - Controle Inteligente de Compensação** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration URLs.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure CIC - Controle Inteligente de Compensação SSO

To configure single sign-on on **CIC - Controle Inteligente de Compensação** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from Microsoft Entra admin center to [CIC - Controle Inteligente de Compensação support team](mailto:cicsso@perdcomp.com.br). They set this setting to have the SAML SSO connection set properly on both sides.

### Create CIC - Controle Inteligente de Compensação test user

In this section, you create a user called B.Simon in CIC - Controle Inteligente de Compensação. Work with [CIC - Controle Inteligente de Compensação support team](mailto:cicsso@perdcomp.com.br) to add the users in the CIC - Controle Inteligente de Compensação platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application** in Microsoft Entra admin center. This option redirects to CIC - Controle Inteligente de Compensação Sign-on URL where you can initiate the login flow.
- Go to CIC - Controle Inteligente de Compensação Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the CIC - Controle Inteligente de Compensação tile in the My Apps, this option redirects to CIC - Controle Inteligente de Compensação Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure CIC - Controle Inteligente de Compensação you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
