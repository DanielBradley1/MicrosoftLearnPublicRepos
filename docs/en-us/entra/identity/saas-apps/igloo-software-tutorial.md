<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/igloo-software-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Igloo Software for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Igloo Software with Microsoft Entra ID. When you integrate Igloo Software with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Igloo Software.
- Enable your users to be automatically signed-in to Igloo Software with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Igloo Software single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Igloo Software supports **SP** initiated SSO.
- Igloo Software supports **Just In Time** user provisioning.

## Add Igloo Software from the gallery

To configure the integration of Igloo Software into Microsoft Entra ID, you need to add Igloo Software from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Igloo Software** in the search box.
4. Select **Igloo Software** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Igloo Software

Configure and test Microsoft Entra SSO with Igloo Software using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Igloo Software.

To configure and test Microsoft Entra SSO with Igloo Software, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Igloo Software SSO](#configure-igloo-software-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Igloo Software test user](#create-igloo-software-test-user)** - to have a counterpart of B.Simon in Igloo Software that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Igloo Software** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** box, type a URL using the following pattern: `https://<company name>.igloocommmunities.com/saml.digest`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<company name>.igloocommmunities.com/saml.digest`

   c. In the **Sign-on URL** text box, type a URL using the following pattern: `https://<company name>.igloocommmunities.com`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [Igloo Software Client support team](https://customercare.igloosoftware.com/) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up Igloo Software** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Igloo Software SSO

1. In a different web browser window, log in to your Igloo Software company site as an administrator.
2. Go to the **Control Panel**.

   ![Control Panel](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/igloo-software-tutorial/settings.png "Control Panel")

3. In the **Membership** tab, select **Sign In Settings**.

   ![Sign in Settings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/igloo-software-tutorial/resource.png "Sign in Settings")

4. In the SAML Configuration section, select **Configure SAML Authentication**.

   ![SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/igloo-software-tutorial/authentication.png "SAML Configuration")

5. In the **General Configuration** section, perform the following steps:

   ![General Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/igloo-software-tutorial/certificate.png "General Configuration")


   a. In the **Connection Name** textbox, type a custom name for your configuration.


   b. In the **IdP Login URL** textbox, paste the value of **Login URL**..


   c. In the **IdP Logout URL** textbox, paste the value of **Logout URL**..


   d. Select **Logout Response and Request HTTP Type** as **POST**.


   e. Open your **base-64** encoded certificate in notepad downloaded from Azure portal, copy the content of it into your clipboard, and then paste it to the **Public Certificate** textbox.

6. In the **Response and Authentication Configuration**, perform the following steps:

   ![Response and Authentication Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/igloo-software-tutorial/response.png "Response and Authentication Configuration")


   a. As **Identity Provider**, select **Microsoft ADFS**.


   b. As **Identifier Type**, select **Email Address**.


   c. In the **Email Attribute** textbox, type **emailaddress**.


   d. In the **First Name Attribute** textbox, type **givenname**.


   e. In the **Last Name Attribute** textbox, type **surname**.

7. Perform the following steps to complete the configuration:

   ![User creation on Sign in](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/igloo-software-tutorial/users.png "User creation on Sign in")


   a. As **User creation on Sign in**, select **Create a new user in your site when they sign in**.


   b. As **Sign in Settings**, select **Use SAML button on “Sign in” screen**.


   c. Select **Save**.

### Create Igloo Software test user

There's no action item for you to configure user provisioning to Igloo Software.

When an assigned user tries to log in to Igloo Software using the access panel, Igloo Software checks whether the user exists. If there is no user account available yet, it's automatically created by Igloo Software.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Igloo Software Sign-on URL where you can initiate the login flow.
- Go to Igloo Software Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Igloo Software tile in the My Apps, this option redirects to Igloo Software Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Igloo Software you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
