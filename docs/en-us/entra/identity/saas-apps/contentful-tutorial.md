<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/contentful-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Contentful for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Contentful with Microsoft Entra ID. When you integrate Contentful with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Contentful.
- Enable your users to be automatically signed-in to Contentful with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Contentful single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Contentful supports **SP and IDP** initiated SSO.
- Contentful supports **Just In Time** user provisioning.
- Contentful supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/contentful-provisioning-tutorial).

Note

The identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Contentful from the gallery

To configure the integration of Contentful into Microsoft Entra ID, you need to add Contentful from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Contentful** in the search box.
4. Select **Contentful** in the results, and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Contentful

Configure and test Microsoft Entra SSO with Contentful using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Contentful.

To configure and test Microsoft Entra SSO with Contentful, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Contentful SSO](#configure-contentful-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Contentful test user](#create-contentful-test-user)** - to have a counterpart of B.Simon in Contentful that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Contentful** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, if you want to configure the application in **IDP** initiated mode, perform the following step:

   a. In the **Reply URL** text box, copy the ACS \(Assertion Consumer Service\) URL from the SSO setup page in Contentful. It will look like this: `https://be.contentful.com/sso/<organization_id>/consume`.
6. Select **Set additional URLs** and perform the following step if you want to configure the application in **SP** initiated mode:

   a. In the **Sign-on URL** text box, copy the same ACS \(Assertion Consumer Service\) URL. It will look like this: `https://be.contentful.com/sso/<organization_id>/login`.

   Note

   These values aren't real. Update these values with the actual Reply URL and Sign-On URL by copying the ACS \(Assertion Consumer Service\) URL from the SSO setup page in Contentful.
7. Contentful application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

8. In addition to above, Contentful application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | email | user.userprincipalname |
9. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

10. In the **Set up Contentful** section, copy the login URL to configure Contentful SSO.

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Contentful SSO

Follow these steps to configure single sign-on on the **Contentful** side.

1. In [Contentful](https://app.contentful.com), navigate to the SSO setup page in **Organization Settings**.
2. Select **Set up SSO**.
3. Copy and paste the login URL from the **Set up Contentful** section in Microsoft Entra ID.
4. Copy and paste the certificate from the Base64 certificate file you downloaded from Microsoft Entra ID.
5. Set up an SSO name for SP-initiated login.
6. Select **Enable SSO**.

If that doesn't work, reach out to the [Contentful support team](mailto:support@contentful.com).

### Create Contentful test user

In this section, a user called B.Simon is created in Contentful. Contentful supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Contentful, a new one is created after authentication.

Contentful also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/contentful-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Contentful Sign on URL where you can initiate the login flow.
- Go to Contentful Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Contentful for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Contentful tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Contentful for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Contentful you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
