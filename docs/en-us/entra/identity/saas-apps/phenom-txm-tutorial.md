<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/phenom-txm-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Phenom TXM for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Phenom TXM with Microsoft Entra ID. When you integrate Phenom TXM with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Phenom TXM.
- Enable your users to be automatically signed-in to Phenom TXM with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Phenom TXM single sign-on \(SSO\) enabled subscription and a user account with the Client Admin role in Service Hub.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Phenom TXM supports **SP** and **IDP** initiated SSO.

## Add Phenom TXM from the gallery

To configure the integration of Phenom TXM into Microsoft Entra ID, you need to add Phenom TXM from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Phenom TXM** in the search box.
4. Select **Phenom TXM** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Phenom TXM

Configure and test Microsoft Entra SSO with Phenom TXM using a test user called **B.Simon**. For SSO to work, you need to establish an assignment relationship between a Microsoft Entra user or group and the related Phenom TXM application, ensuring that Microsoft Entra ID passes the user's email address to Phenom TXM as a user identifier.

To configure and test Microsoft Entra SSO with Phenom TXM, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Phenom TXM SSO](#configure-phenom-txm-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Phenom TXM test user](#create-phenom-txm-test-user)** - to have a counterpart of B.Simon in Phenom TXM that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Phenom TXM** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, enter the **ENTITY ID** copied from Service Hub.

   b. In the **Reply URL** text box, enter the **Redirect URI \(ACS URL\)** copied from Service Hub.

   1. In the first **Reply URL** text box, enter the **Redirect URI \(ACS URL\)** copied from Service Hub and set the Index value to **0**.
   2. In the second **Reply URL** text box, enter the **Redirect URI \(ACS URL\) SP Initiated Flow** copied from Service Hub and set the Index value to **1**


   Note


   Ensure that the first **Reply URL** is set as the **Default** using the checkbox.

6. Perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign on URL** text box, type one of the following URLs:

   | Environment | Sign on URL |
   | --- | --- |
   | Staging | `https://login-stg.phenompro.com` |
   | Production | `https://login.phenom.com` |

7. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Phenom TXM SSO

1. Log in to your Phenom TXM instance Service Hub as a user with the Client Admin role.
2. Go to **Settings** tab > **Identity Provider**.
3. In the **Identity Provider** section, perform the following steps:

   ![Screenshot that shows the Configuration Settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/phenom-txm-tutorial/input.png "Configuration")


   ![Screenshot that shows the Identity Provider Metadata.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/phenom-txm-tutorial/certificate.png "Metadata")


   a. Choose **SAML** from the dropdown selector.


   b. Enter a valid name in the **Display Name** textbox.


   c. In the **Single SignOn URL** textbox, paste the **Login URL** value, which you've copied.


   d. In the **Meta data URL** textbox, paste the **App Federation Metadata Url** value, which you've copied.


   e. Copy **Entity ID** value, paste this value into the **Identifier** text box in the **Basic SAML Configuration** section.


   f. Copy **Redirect URI \(ACS URL\)** value, paste this value into the first **Reply URL** text box in the **Basic SAML Configuration** section.


   g. Copy **Redirect URI \(ACS URL\) SP Initiated Flow** value, paste this value into the second **Reply URL** text box in the **Basic SAML Configuration** section.

### Create Phenom TXM test user

1. In a different web browser window, log in to your Phenom TXM website as an administrator.
2. Go to **Users** tab and select **Create Users** > **Create single new User**.
3. In the **Create User** page, perform the following steps:

   a. In the **User Information** section, enter a valid **First Name**, **Last Name** and **Work Email** in the textboxes and select **Continue**.

   ![Screenshot that shows the User Information fields.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/phenom-txm-tutorial/name.png "User Information")


   b. In the **Assign Tenants** section, **Select Tenants** and select **Continue**.


   ![Screenshot that shows the Tenants Information fields.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/phenom-txm-tutorial/details.png "Tenants")


   c. In the **Assign Roles** section, **Select roles** from the dropdown and select **Continue**.


   ![Screenshot that shows the Roles Mapping for Users.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/phenom-txm-tutorial/role.png "Mapping")


   d. In the **Summary** section, review your selections and select **Finish** to create a user.


   ![Screenshot that shows the Phenom TXM Summary section.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/phenom-txm-tutorial/finish.png "Summary")

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Phenom TXM Sign-on URL where you can initiate the login flow.
- Go to Phenom TXM Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Phenom TXM for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Phenom TXM tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Phenom TXM for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Phenom TXM you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
