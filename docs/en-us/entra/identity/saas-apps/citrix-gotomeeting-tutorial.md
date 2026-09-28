<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/citrix-gotomeeting-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure GoToMeeting for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate GoToMeeting with Microsoft Entra ID. When you integrate GoToMeeting with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to GoToMeeting.
- Enable your users to be automatically signed-in to GoToMeeting with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- GoToMeeting single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- GoToMeeting supports **IDP** initiated SSO.
- GoToMeeting supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/citrixgotomeeting-provisioning-tutorial).

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add GoToMeeting from the gallery

To configure the integration of GoToMeeting into Microsoft Entra ID, you need to add GoToMeeting from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **GoToMeeting** in the search box.
4. Select **GoToMeeting** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for GoToMeeting

Configure and test Microsoft Entra SSO with GoToMeeting using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in GoToMeeting.

To configure and test Microsoft Entra SSO with GoToMeeting, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure GoToMeeting SSO](#configure-gotomeeting-sso)** - to configure the single sign-on settings on application side.

   1. **[Create GoToMeeting test user](#create-gotomeeting-test-user)** - to have a counterpart of B.Simon in GoToMeeting that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **GoToMeeting** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type the URL: `https://authentication.logmeininc.com/saml/sp`

   b. In the **Reply URL** text box, type the URL: `https://authentication.logmeininc.com/saml/acs`

   c. Select **set additional URLs** and configure the below URLs

   d. **Sign on URL** \(keep this blank\)

   e. In the **RelayState** text box, type one of the following URLs:

   - For GoToMeeting App, use `https://global.gotomeeting.com`
   - For GoToTraining, use `https://global.gototraining.com`
   - For GoToWebinar, use `https://global.gotowebinar.com`
   - For GoToAssist, use `https://app.gotoassist.com`

6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up GoToMeeting** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure GoToMeeting SSO

1. In a different browser window, log in to your [GoToMeeting Organization Center](https://organization.logmeininc.com/). You be prompted to confirm that the IdP has been updated.
2. Enable the "My Identity Provider has been updated with the new domain" checkbox. Select **Done** when finished.

### Create GoToMeeting test user

In this section, a user called Britta Simon is created in GoToMeeting. GoToMeeting supports just-in-time provisioning, which is enabled by default.

There's no action item for you in this section. If a user doesn't already exist in GoToMeeting, a new one is created when you attempt to access GoToMeeting.

Note

If you need to create a user manually, Contact [GoToMeeting support team](https://support.logmeininc.com/gotomeeting).

Note

GoToMeeting also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/citrixgotomeeting-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the GoToMeeting for which you set up the SSO.
- You can use Microsoft My Apps. When you select the GoToMeeting tile in the My Apps, you should be automatically signed in to the GoToMeeting for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure GoToMeeting you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
