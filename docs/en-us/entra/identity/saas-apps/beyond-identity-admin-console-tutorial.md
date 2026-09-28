<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/beyond-identity-admin-console-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Beyond Identity Admin Console for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Beyond Identity Admin Console with Microsoft Entra ID. When you integrate Beyond Identity Admin Console with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Beyond Identity Admin Console.
- Enable your users to be automatically signed-in to Beyond Identity Admin Console with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Beyond Identity Admin Console single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Beyond Identity Admin Console supports **SP** initiated SSO.

## Add Beyond Identity Admin Console from the gallery

To configure the integration of Beyond Identity Admin Console into Microsoft Entra ID, you need to add Beyond Identity Admin Console from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Beyond Identity Admin Console** in the search box.
4. Select **Beyond Identity Admin Console** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Beyond Identity Admin Console

Configure and test Microsoft Entra SSO with Beyond Identity Admin Console using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Beyond Identity Admin Console.

To configure and test Microsoft Entra SSO with Beyond Identity Admin Console, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Beyond Identity Admin Console SSO](#configure-beyond-identity-admin-console-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Beyond Identity Admin Console test user](#create-beyond-identity-admin-console-test-user)** - to have a counterpart of B.Simon in Beyond Identity Admin Console that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Beyond Identity Admin Console** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://admin.byndid.com/auth/saml/<azure-tenant-id>/sso/metadata.xml`

   b. In the **Sign on URL** text box, type a URL using the following pattern: `https://admin.byndid.com/auth/?org_id=<bi-tenant-id>`

   Note

   These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [Beyond Identity Admin Console Client support team](mailto:support@beyondidentity.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. Beyond Identity Admin Console application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

7. In addition to above, Beyond Identity Admin Console application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Namespace | Source Attribute |
   | --- | --- | --- |
   | immutableId | externalId | user.immutableId |
8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

9. On the **Set up Beyond Identity Admin Console** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Beyond Identity Admin Console SSO

To configure single sign-on on **Beyond Identity Admin Console** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Beyond Identity Admin Console support team](mailto:support@beyondidentity.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Beyond Identity Admin Console test user

In this section, you create a user called Britta Simon in Beyond Identity Admin Console. Work with [Beyond Identity Admin Console support team](mailto:support@beyondidentity.com) to add the users in the Beyond Identity Admin Console platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Beyond Identity Admin Console Sign-on URL where you can initiate the login flow.
- Go to Beyond Identity Admin Console Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Beyond Identity Admin Console tile in the My Apps, this option redirects to Beyond Identity Admin Console Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Beyond Identity Admin Console you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
