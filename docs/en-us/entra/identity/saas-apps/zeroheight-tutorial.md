<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/zeroheight-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure zeroheight for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate zeroheight with Microsoft Entra ID. When you integrate zeroheight with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to zeroheight.
- Enable your users to be automatically signed-in to zeroheight with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- zeroheight single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- zeroheight supports **SP** initiated SSO.

## Add zeroheight from the gallery

To configure the integration of zeroheight into Microsoft Entra ID, you need to add zeroheight from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **zeroheight** in the search box.
4. Select **zeroheight** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for zeroheight

Configure and test Microsoft Entra SSO with zeroheight using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in zeroheight.

To configure and test Microsoft Entra SSO with zeroheight, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure zeroheight SSO](#configure-zeroheight-sso)** - to configure the single sign-on settings on application side.

   1. **[Create zeroheight test user](#create-zeroheight-test-user)** - to have a counterpart of B.Simon in zeroheight that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **zeroheight** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a value using the following pattern: `zeroheight:<CUSTOM_ID>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://zeroheight.com/sso/acs/<CUSTOM_ID>`

   c. In the **Sign on URL** text box, type the URL: `https://zeroheight.com/sso`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. These values are generated for you in your account. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. The zeroheight application expects the SAML assertions in a specific format and requires you to add custom attribute mappings to your SAML token attributes configuration. Find the following section with the default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

7. zeroheight doesn't use any of the default attributes. Instead, add the following attributes to be passed back in SAML response. These attributes should also be pre-populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | email | user.mail |
   | FirstName | user.givenname |
8. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure zeroheight SSO

To configure single sign-on on **zeroheight** side, you need to paste the **App Federation Metadata Url** into your browser and download the XML file. Then you need to extract the Identity Provider Single Sign-On URL and X.509 Certificate from it. Ask your IT team if you're unsure.

### Create zeroheight test user

In this section, you create a user called Britta Simon in zeroheight. Work with [zeroheight support team](mailto:support@zeroheight.com) to add the users in the zeroheight platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to zeroheight Sign-on URL where you can initiate the login flow.
- Go to zeroheight Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the zeroheight tile in the My Apps, this option redirects to zeroheight Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure zeroheight you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
