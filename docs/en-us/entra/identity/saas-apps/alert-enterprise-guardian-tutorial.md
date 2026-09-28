<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/alert-enterprise-guardian-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure AlertEnterprise-Guardian for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate AlertEnterprise-Guardian with Microsoft Entra ID. Application automates the identity management lifecycle. Built-in Regulatory Compliance ensures controls are in place before granting access to identities. When you integrate AlertEnterprise-Guardian with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to AlertEnterprise-Guardian.
- Enable your users to be automatically signed-in to AlertEnterprise-Guardian with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for AlertEnterprise-Guardian in a test environment. AlertEnterprise-Guardian supports **IDP** initiated single sign-on.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Prerequisites

To integrate Microsoft Entra ID with AlertEnterprise-Guardian, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- AlertEnterprise-Guardian single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the AlertEnterprise-Guardian application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add AlertEnterprise-Guardian from the Microsoft Entra gallery

Add AlertEnterprise-Guardian from the Microsoft Entra application gallery to configure single sign-on with AlertEnterprise-Guardian. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **AlertEnterprise-Guardian** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type the value: `urn:mace:saml:pac4j.org`

   b. In the **Reply URL** textbox, type a URL using the following pattern: `https://<SUBDOMAIN>.alerthsc.com/api/auth/sso/callback?client_name=<Client_Name>`

   Note

   The Reply URL isn't real. Update this value with the actual Reply URL. Contact [AlertEnterprise-Guardian support team](mailto:info@alertenterprise.com) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. AlertEnterprise-Guardian application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Image")

7. In addition to above, AlertEnterprise-Guardian application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | tenant | <Share\_By\_ALERT\_Team> |
8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

## Configure AlertEnterprise-Guardian SSO

To configure single sign-on on **AlertEnterprise-Guardian** side, you need to send the **App Federation Metadata Url** to [AlertEnterprise-Guardian support team](mailto:info@alertenterprise.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create AlertEnterprise-Guardian test user

In this section, you create a user called Britta Simon at AlertEnterprise-Guardian. Work with [AlertEnterprise-Guardian support team](mailto:info@alertenterprise.com) to add the users in the AlertEnterprise-Guardian platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the AlertEnterprise-Guardian for which you set up the SSO.
- You can use Microsoft My Apps. When you select the AlertEnterprise-Guardian tile in the My Apps, you should be automatically signed in to the AlertEnterprise-Guardian for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure AlertEnterprise-Guardian you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
