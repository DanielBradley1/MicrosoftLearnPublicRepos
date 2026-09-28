<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/campus-cafe-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Campus Café for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Campus Café with Microsoft Entra ID. When you integrate Campus Café with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Campus Café.
- Enable your users to be automatically signed-in to Campus Café with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Campus Café single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Campus Café supports **SP** initiated SSO.

## Add Campus Café from the gallery

To configure the integration of Campus Café into Microsoft Entra ID, you need to add Campus Café from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Campus Café** in the search box.
4. Select **Campus Café** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Campus Café

Configure and test Microsoft Entra SSO with Campus Café using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Campus Café.

To configure and test Microsoft Entra SSO with Campus Café, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Campus Café SSO](#configure-campus-cafe-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Campus Café test user](#create-campus-cafe-test-user)** - to have a counterpart of B.Simon in Campus Café that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Campus Café** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you have **Service Provider metadata file**, perform the following steps:

   a. Select **Upload metadata file**.

   ![Upload metadata file](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/upload-metadata.png)


   b. Select **folder logo** to select the metadata file and select **Upload**.


   ![choose metadata file](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/browse-upload-metadata.png)


   c. After the metadata file is successfully uploaded, the **Identifier** value gets auto populated in **Basic SAML Configuration** section.


   In the **Sign-on URL** text box, type a URL using the following pattern: `https://{SSO}-web.scansoftware.com/cafeweb/loginsso`


   Note


   If the **Identifier** value doesn't get auto populated, then please fill in the value manually according to your requirement. The Sign-on URL value isn't real. Update this value with the actual Sign-on URL. Contact [Campus Café Client support team](mailto:support@campuscafesoftware.com) to get this value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up Campus Café** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Campus Cafe SSO

To configure single sign-on on **Campus Café** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Campus Café support team](mailto:support@campuscafesoftware.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Campus Cafe test user

In this section, you create a user called B.Simon in Campus Café. Work with [Campus Café support team](mailto:support@campuscafesoftware.com) to add the users in the Campus Café platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Campus Cafe Sign-on URL where you can initiate the login flow.
- Go to Campus Cafe Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Campus Cafe tile in the My Apps, this option redirects to Campus Cafe Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Campus Cafe you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
