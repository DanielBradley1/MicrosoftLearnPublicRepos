<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/autodesk-sso-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Autodesk SSO for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Autodesk SSO with Microsoft Entra ID. When you integrate Autodesk SSO with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Autodesk SSO.
- Enable your users to be automatically signed-in to Autodesk SSO with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Autodesk SSO single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Autodesk SSO supports **SP** initiated SSO.
- Autodesk SSO supports **Just In Time** user provisioning.
- Autodesk SSO supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/autodesk-sso-provisioning-tutorial).

## Adding Autodesk SSO from the gallery

To configure the integration of Autodesk SSO into Microsoft Entra ID, you need to add Autodesk SSO from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Autodesk SSO** in the search box.
4. Select **Autodesk SSO** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Autodesk SSO

Configure and test Microsoft Entra SSO with Autodesk SSO using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Autodesk SSO.

To configure and test Microsoft Entra SSO with Autodesk SSO, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Autodesk SSO](#configure-autodesk-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Autodesk SSO test user](#create-autodesk-sso-test-user)** - to have a counterpart of B.Simon in Autodesk SSO that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Autodesk SSO** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, enter the values for the following fields:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://www.okta.com/saml2/service-provider/<UNIQUE_ID>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://autodesk-prod.okta.com/sso/saml2/<UNIQUE_ID>`

   c. In the **Sign on URL** text box, type the URL: `https://autodesk-prod.okta.com/sso/saml2/`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Autodesk SSO Client support team](https://knowledge.autodesk.com/contact-support) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. Autodesk SSO application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

7. In addition to above, Autodesk SSO application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | firstName | user.givenname |
   | lastName | user.surname |
   | objectGUID | user.objectid |
   | email | user.mail |
8. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

9. On the **Set up Autodesk SSO** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Autodesk SSO

To configure single sign-on on **Autodesk SSO** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Autodesk SSO support team](https://knowledge.autodesk.com/contact-support). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Autodesk SSO test user

In this section, a user called Britta Simon is created in Autodesk SSO. Autodesk SSO supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Autodesk SSO, a new one is created after authentication.

## Test SSO

To test the Autodesk SSO, open the Autodesk console and select **Test Connection** button and authenticate using the test account which you have created in the **Create a Microsoft Entra test user** section.

## Related content

Once you configure Autodesk SSO you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
