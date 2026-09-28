<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/myawardpoints-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure My Award Points Top Sub/Top Team for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate My Award Points Top Sub/Top Team with Microsoft Entra ID. When you integrate My Award Points Top Sub/Top Team with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to My Award Points Top Sub/Top Team.
- Enable your users to be automatically signed-in to My Award Points Top Sub/Top Team with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- My Award Points Top Sub/Top Team single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- My Award Points Top Sub/Top Team supports **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add My Award Points Top Sub/Top Team from the gallery

To configure the integration of My Award Points Top Sub/Top Team into Microsoft Entra ID, you need to add My Award Points Top Sub/Top Team from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **My Award Points Top Sub/Top Team** in the search box.
4. Select **My Award Points Top Sub/Top Team** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for My Award Points Top Sub/Top Team

Configure and test Microsoft Entra SSO with My Award Points Top Sub/Top Team using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in My Award Points Top Sub/Top Team.

To configure and test Microsoft Entra SSO with My Award Points Top Sub/Top Team, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure My Award Points Top Sub/Top Team SSO](#configure-my-award-points-top-subtop-team-sso)** - to configure the single sign-on settings on application side.

   1. **[Create My Award Points Top Sub/Top Team test user](#create-my-award-points-top-subtop-team-test-user)** - to have a counterpart of B.Simon in My Award Points Top Sub/Top Team that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **My Award Points Top Sub/Top Team** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following step:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://microsoftrr.performnet.com/biwv1auth/Shibboleth.sso/Login?providerId=<Azure AD Identifier>`

   Note

   The value isn't real. You get the `<Azure AD Identifier>` value in the later steps in this article.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up My Award Points Top Sub/Top Team** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)


   Note


   Append the copied Microsoft Entra Identifier value with the Sign on URL in the place of `<Azure AD Identifier>` in the **Basic SAML Configuration** section.

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure My Award Points Top Sub/Top Team SSO

To configure single sign-on on **My Award Points Top Sub/Top Team** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [My Award Points Top Sub/Top Team support team](mailto:myawardpoints@biworldwide.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create My Award Points Top Sub/Top Team test user

In this section, you create a user called Britta Simon in My Award Points Top Sub/Top Team. Work with [My Award Points Top Sub/Top Team support team](mailto:myawardpoints@biworldwide.com) to add the users in the My Award Points Top Sub/Top Team platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to My Award Points Top Sub/Top Team Sign-on URL where you can initiate the login flow.
- Go to My Award Points Top Sub/Top Team Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the My Award Points Top Sub/Top Team tile in the My Apps, this option redirects to My Award Points Top Sub/Top Team Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure My Award Points Top Sub/Top Team you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
