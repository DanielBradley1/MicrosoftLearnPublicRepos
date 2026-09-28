<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/sifulan-connect-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-18 -->

# Configure SIFULAN Connect for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate SIFULAN Connect with Microsoft Entra ID. When you integrate SIFULAN Connect with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to SIFULAN Connect.
- Enable your users to be automatically signed-in to SIFULAN Connect with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- SIFULAN Connect single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- SIFULAN Connect supports **SP** initiated SSO.

## Add SIFULAN Connect from the gallery

To configure the integration of SIFULAN Connect into Microsoft Entra ID, you need to add SIFULAN Connect from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **SIFULAN Connect** in the search box.
4. Select **SIFULAN Connect** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for SIFULAN Connect

Configure and test Microsoft Entra SSO with SIFULAN Connect using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in SIFULAN Connect.

To configure and test Microsoft Entra SSO with SIFULAN Connect, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Create a Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure SIFULAN Connect SSO](#configure-sifulan-connect-sso)** - to configure the single sign-on settings on application side.

   1. **[Create SIFULAN Connect test user](#create-sifulan-connect-test-user)** - to have a counterpart of B.Simon in SIFULAN Connect that's linked to the Microsoft Entra ID representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **SIFULAN Connect** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://<Sub-DomainName>/idp/shibboleth`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<Sub-DomainName>/idp/shibboleth`

   c. In the **Sign on URL** text box, type a URL using the following pattern: `https://<Sub-DomainName>/idp/profile/SAML2/POST/SSO`

   Note

   These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [SIFULAN Connect support team](mailto:support@sifulan.my) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.
6. SIFULAN Connect application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Image")

7. In addition to above, SIFULAN Connect application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | groups | user.groups |
   | urn:oid:2.16.840.1.113730.3.1.3 | user.employeeid |
8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

9. On the **Set up SIFULAN Connect** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows copy configuration URLs.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Configuration")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure SIFULAN Connect SSO

To configure single sign-on on **SIFULAN Connect** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from Microsoft Entra admin center to [SIFULAN Connect support team](mailto:support@sifulan.my). They set this setting to have the SAML SSO connection set properly on both sides.

### Create SIFULAN Connect test user

In this section, you create a user called B.Simon in SIFULAN Connect. Work with [SIFULAN Connect support team](mailto:support@sifulan.my) to add the users in the SIFULAN Connect platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration using the My Apps.

#### SP initiated:

- Select **Test this application** in Microsoft Entra admin center. this option redirects to SIFULAN Connect Sign on URL where you can initiate the login flow.
- Go to SIFULAN Connect Sign-on URL directly and initiate the login flow from there.

## Related content

Once you configure SIFULAN Connect you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
