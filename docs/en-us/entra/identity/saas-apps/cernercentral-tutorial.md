<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/cernercentral-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Cerner Central for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Cerner Central with Microsoft Entra ID. When you integrate Cerner Central with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Cerner Central.
- Enable your users to be automatically signed-in to Cerner Central with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Cerner Central single sign-on enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Cerner Central supports **IDP** initiated SSO.
- Cerner Central supports [**Automated** user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/cernercentral-provisioning-tutorial).

## Add Cerner Central from the gallery

To configure the integration of Cerner Central into Microsoft Entra ID, you need to add Cerner Central from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Cerner Central** in the search box.
4. Select **Cerner Central** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Cerner Central

Configure and test Microsoft Entra SSO with Cerner Central using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Cerner Central.

To configure and test Microsoft Entra SSO with Cerner Central, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Cerner Central SSO](#configure-cerner-central-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Cerner Central test user](#create-cerner-central-test-user)** - to have a counterpart of B.Simon in Cerner Central that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Cerner Central** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type a URL using one of the following patterns:

   | **Identifier** |
   | --- |
   | `https://<instancename>.cernercentral.com/session-api/protocol/saml2/metadata` |
   | `https://<instancename>.sandboxcernercentral.com/session-api/protocol/saml2/metadata` |


   b. In the **Reply URL** text box, type a URL using one of the following patterns:


   | **Reply URL** |
   | --- |
   | `https://<instancename>.cernercentral.com/session-api/protocol/saml2/sso` |
   | `https://<instancename>.sandboxcernercentral.com/session-api/protocol/saml2/sso` |


   Note


   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Cerner Central Client support team](mailto:SISupport@cbre.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up Single Sign-On with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Cerner Central SSO

To configure single sign-on on **Cerner Central** side, you need to send the **App Federation Metadata Url** to [Cerner Central support team](mailto:SISupport@cbre.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Cerner Central test user

**Cerner Central** application allows authentication from any federated identity provider. If a user is able to sign in to the application home page, they are federated and have no need for any manual provisioning. You can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/cernercentral-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the Cerner Central for which you set up the SSO.
- You can use Microsoft My Apps. When you select the Cerner Central tile in the My Apps, you should be automatically signed in to the Cerner Central for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Cerner Central you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
