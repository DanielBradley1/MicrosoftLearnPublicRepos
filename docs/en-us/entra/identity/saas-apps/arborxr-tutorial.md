<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/arborxr-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure ArborXR for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate ArborXR with Microsoft Entra ID. When you integrate ArborXR with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to ArborXR.
- Enable your users to be automatically signed-in to ArborXR with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- ArborXR single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- ArborXR supports **SP** initiated SSO.

## Add ArborXR from the gallery

To configure the integration of ArborXR into Microsoft Entra ID, you need to add ArborXR from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **ArborXR** in the search box.
4. Select **ArborXR** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for ArborXR

Configure and test Microsoft Entra SSO with ArborXR using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in ArborXR.

To configure and test Microsoft Entra SSO with ArborXR, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Create a Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure ArborXR SSO](#configure-arborxr-sso)** - to configure the single sign-on settings on application side.

   1. **[Create ArborXR test user](#create-arborxr-test-user)** - to have a counterpart of B.Simon in ArborXR that's linked to the Microsoft Entra ID representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **ArborXR** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://api.xrdm.app/auth/realms/<INSTANCE>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://api.xrdm.app/auth/realms/<INSTANCE>/broker/SAML2/endpoint`

   c. In the **Sign on URL** text box, type a URL using the following pattern: `https://api.xrdm.app/auth/realms/<INSTANCE>`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [ArborXR support team](mailto:support@arborxr.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.
6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure ArborXR SSO

1. Log in to ArborXR company site as an administrator.
2. Go to **Settings** > **Single Sign-On** > and select **SAML**.
3. In the **Hosted IdP Metadata URL** textbox, paste the **App Federation Metadata Url**, which you have copied from the Microsoft Entra admin center.

   ![Screenshot shows settings of the configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/arborxr-tutorial/settings.png "Account")

4. Select **Apply Changes**.

### Create ArborXR test user

1. In a different web browser window, sign into ArborXR website as an administrator.
2. Navigate to **Settings** > **Users** and select **Add Users**.

   ![Screenshot shows how to create users in application.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/arborxr-tutorial/create.png "Users")

3. In the **Add Users** section, perform the following steps:

   ![Screenshot shows how to create new users in the page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/arborxr-tutorial/details.png "Creating Users")


   1. Select **Role** from the drop-down.
   2. Enter a valid email address in the **Invite via email** textbox.
   3. Select **Invite**.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application** in Microsoft Entra admin center. this option redirects to ArborXR Sign-on URL where you can initiate the login flow.
- Go to ArborXR Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the ArborXR tile in the My Apps, this option redirects to ArborXR Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure ArborXR you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
