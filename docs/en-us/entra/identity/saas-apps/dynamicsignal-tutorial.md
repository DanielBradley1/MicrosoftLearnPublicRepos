<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/dynamicsignal-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Dynamic Signal for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Druva with Microsoft Entra ID. When you integrate Druva with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Druva.
- Enable your users to be automatically signed-in to Druva with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Dynamic Signal single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Dynamic Signal supports **SP** initiated SSO.
- Dynamic Signal supports **Just In Time** user provisioning.
- Dynamic Signal supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/dynamic-signal-provisioning-tutorial).

## Add Druva from the gallery

To configure the integration of Druva into Microsoft Entra ID, you need to add Druva from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Druva** in the search box.
4. Select **Druva** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Druva

Configure and test Microsoft Entra SSO with Druva using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Druva.

To configure and test Microsoft Entra SSO with Druva, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
   2. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.

2. **[Configure Dynamic SSO](#configure-dynamic-signal-sso)** - to configure the Single Sign-On settings on application side.

   1. **[Create Dynamic Signal test user](#create-dynamic-signal-test-user)** - to have a counterpart of Britta Simon in Dynamic Signal that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Dynamic Signal** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Sign-on URL** text box, type a URL using the following pattern: `https://<subdomain>.voicestorm.com`

   b. In the **Identifier** box, type a URL using the following pattern: `https://<subdomain>.voicestorm.com`

   c. In the **Reply URL** text box, type a URL using the following pattern: `https://<subdomain>.voicestorm.com/User/SsoResponse`

   Note

   These values aren't real. Update these values with the actual Sign-On URL, Identifier and Reply URL. Contact [Dynamic Signal Client support team](mailto:support@dynamicsignal.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up Dynamic Signal** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Dynamic Signal SSO

To configure single sign-on on **Dynamic Signal** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Dynamic Signal support team](mailto:support@dynamicsignal.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Dynamic Signal test user

In this section, a user called Britta Simon is created in Dynamic Signal. Dynamic Signal supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Dynamic Signal, a new one is created after authentication.

Dynamic Signal also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/dynamic-signal-provisioning-tutorial) on how to configure automatic user provisioning.

### Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Dynamic Signal Sign-on URL where you can initiate the login flow.
- Go to Dynamic Signal Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Dynamic Signal tile in the My Apps, this option redirects to Dynamic Signal Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Dynamic Signal you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
