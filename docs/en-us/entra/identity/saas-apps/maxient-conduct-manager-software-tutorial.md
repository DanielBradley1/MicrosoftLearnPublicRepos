<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/maxient-conduct-manager-software-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Maxient Conduct Manager Software for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Maxient Conduct Manager Software with Microsoft Entra ID. When you integrate Maxient Conduct Manager Software with Microsoft Entra ID, you can:

- Utilize Microsoft Entra ID to authenticate your users for the Maxient Conduct Manager Software.
- Enable your users to be automatically signed-in to Maxient Conduct Manager Software with their Microsoft Entra accounts.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Maxient Conduct Manager Software single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure your Microsoft Entra ID for use with Maxient Conduct Manager Software.

- Maxient Conduct Manager Software supports **SP and IDP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Maxient Conduct Manager Software from the gallery

To configure the integration of Maxient Conduct Manager Software into Microsoft Entra ID, you need to add Maxient Conduct Manager Software from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Maxient Conduct Manager Software** in the search box.
4. Select **Maxient Conduct Manager Software** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Maxient Conduct Manager Software

Configure and test Microsoft Entra SSO with Maxient Conduct Manager Software. For SSO to work, you need to establish a connection between Microsoft Entra ID and the Maxient Conduct Manager Software.

To configure and test Microsoft Entra SSO with Maxient Conduct Manager Software, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to authenticate for use with the Maxient Conduct Manager Software.

   1. **[Set "User Assignment Required?" to No](#set-user-assignment-required-to-no)** - to allow everyone at your institution to be able to authenticate.

2. **[Test Microsoft Entra Setup With Maxient](#test-with-maxient)** - to verify whether the configuration works, and the correct attributes are being released.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Maxient Conduct Manager Software** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section the application is pre-configured in **IDP** initiated mode and the necessary URLs are already pre-populated with Azure. The user needs to save the configuration by selecting the **Save** button.
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://cm.maxient.com/<SCHOOLCODE>`

   Note

   The value isn't real. Update the value with the actual Sign-on URL. Work with your Maxient Implementation/Support representative to get the value.
7. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer. You need to provide your Maxient Implementation/Support representative with this URL.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Set "User Assignment Required?" to No

It's important to note that this step is **REQUIRED** for Maxient to function properly. Maxient leverages your Microsoft Entra system to *authenticate* users. The *authorization* of users is performed within the Maxient system for the particular function they’re trying to perform. Maxient doesn't use attributes from your directory to make those decisions.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Maxient Conduct Manager Software**.
3. In the app's overview page, toggle the "User Assignment Required" setting to No.

## Test with Maxient

If a support ticket has not already been opened with a Maxient Implementation/Support representative, send an email to [support@maxient.com](mailto:support@maxient.com) with the subject "Campus Based Authentication/Azure Setup - <<School Name>>". In the body of the email, provide the **App Federation Metadata Url**. Maxient staff will respond with a test link to verify the proper attributes are being released.

## Related content

Once you configure Maxient Conduct Manager Software you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
