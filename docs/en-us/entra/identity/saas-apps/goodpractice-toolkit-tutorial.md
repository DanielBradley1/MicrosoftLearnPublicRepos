<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/goodpractice-toolkit-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Mind Tools Toolkit for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Mind Tools Toolkit with Microsoft Entra ID. When you integrate Mind Tools Toolkit with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Mind Tools Toolkit.
- Enable your users to be automatically signed in to Mind Tools Toolkit \(single sign-on\) with their Microsoft Entra accounts.
- Manage your accounts in one central location: the Azure portal.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A Mind Tools Toolkit subscription with single sign-on \(SSO\) enabled.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Mind Tools Toolkit supports SP-initiated SSO.
- Mind Tools Toolkit supports just-in-time user provisioning.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Mind Tools Toolkit from the gallery

To configure the integration of Mind Tools Toolkit into Microsoft Entra ID, you need to add Mind Tools Toolkit from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, enter **Mind Tools Toolkit** in the search box.
4. Select **Mind Tools Toolkit** from the search results, and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Mind Tools Toolkit

Configure and test Microsoft Entra SSO with Mind Tools Toolkit using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Mind Tools Toolkit.

To configure and test Microsoft Entra SSO with Mind Tools Toolkit, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Mind Tools Toolkit SSO](#configure-mind-tools-toolkit-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Mind Tools Toolkit test user](#create-mind-tools-toolkit-test-user)** - to have a counterpart of B.Simon in Mind Tools Toolkit that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Mind Tools Toolkit** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, in the **Sign-on URL** box, enter a URL having the pattern `https://app.goodpractice.net/#/<subscriptionUrl>/s/<LOCATION_ID>`.

   Note

   The **Sign-on URL** value isn't real. Update the value with the actual sign-on URL. Contact the [Mind Tools Toolkit Client support team](mailto:support@goodpractice.com) to get the value.
6. On the **Set-up Single Sign-On with SAML** page, go to the **SAML Signing Certificate** section. To the right of **Federation Metadata XML**, select **Download** to download the XML text and save it on your computer. The XML contents depend on the options you select.

   ![The SAML Signing Certificate section, with Download highlighted next to Federation Metadata XML](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. In the **Set up Mind Tools Toolkit** section, copy whichever of the following URLs you need.

   ![The Set up Mind Tools Toolkit section, with the configuration URLs highlighted](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Mind Tools Toolkit SSO

To configure single sign-on on the **Mind Tools Toolkit** side, send the downloaded **Federation Metadata XML** text and the previously copied URLs to the [Mind Tools Toolkit support team](mailto:support@goodpractice.com). They configure this setting to have the SAML SSO connection set properly on both sides.

### Create Mind Tools Toolkit test user

In this section, a user called B.Simon is created in Mind Tools Toolkit. Mind Tools Toolkit supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Mind Tools Toolkit, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Mind Tools Toolkit Sign-on URL where you can initiate the login flow.
- Go to Mind Tools Toolkit Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Mind Tools Toolkit tile in the My Apps, this option redirects to Mind Tools Toolkit Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Mind Tools Toolkit you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
