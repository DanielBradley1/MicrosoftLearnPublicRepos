<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/filecloud-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure FileCloud for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate FileCloud with Microsoft Entra ID. When you integrate FileCloud with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to FileCloud.
- Enable your users to be automatically signed-in to FileCloud with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- FileCloud single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- FileCloud supports **SP** initiated SSO.
- FileCloud supports **Just In Time** user provisioning.

## Add FileCloud from the gallery

To configure the integration of FileCloud into Microsoft Entra ID, you need to add FileCloud from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **FileCloud** in the search box.
4. Select **FileCloud** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for FileCloud

Configure and test Microsoft Entra SSO with FileCloud using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in FileCloud.

To configure and test Microsoft Entra SSO with FileCloud, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure FileCloud SSO](#configure-filecloud-sso)** - to configure the single sign-on settings on application side.

   1. **[Create FileCloud test user](#create-filecloud-test-user)** - to have a counterpart of B.Simon in FileCloud that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **FileCloud** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Sign on URL** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.filecloudonline.com`

   b. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.filecloudonline.com/simplesaml/module.php/saml/sp/metadata.php/default-sp`

   Note

   These values aren't real. Update these values with the actual Sign on URL and Identifier. Contact [FileCloud Client support team](mailto:support@codelathe.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up FileCloud** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure FileCloud SSO

1. In a different web browser window, sign-on to your FileCloud tenant as an administrator.
2. On the left navigation pane, select **Settings**.

   ![Screenshot that shows "Settings" highlighted in the left navigation pane.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/filecloud-tutorial/setting.png)

3. Select **SSO** tab on Settings section.

   ![Screenshot that shows the "Settings" section with the "S S O" tab selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/filecloud-tutorial/tab.png)

4. Select **SAML** as **Default SSO Type** on **Single Sign On \(SSO\) Settings** panel.

   ![Screenshot that shows the "Single Sign On \(S S O\) Settings" panel with "S A M L" selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/filecloud-tutorial/panel.png)

5. In the **IdP End Point URL** textbox, paste the value of **Microsoft Entra Identifier**..

   ![Screenshot that shows the "S A M L Settings" section with "I d P End Point U R L" highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/filecloud-tutorial/identifier.png)

6. Open your downloaded metadata file in notepad, copy the content of it into your clipboard, and then paste it to the **IdP Meta Data** textbox on **SAML Settings** panel.

   ![Configure Single Sign-On On App side](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/filecloud-tutorial/metadata.png)

7. Select **Save** button.

### Create FileCloud test user

In this section, a user called Britta Simon is created in FileCloud. FileCloud supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in FileCloud, a new one is created after authentication.

Note

If you need to create a user manually, you need to contact the [FileCloud Client support team](mailto:support@codelathe.com).

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to FileCloud Sign-on URL where you can initiate the login flow.
- Go to FileCloud Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the FileCloud tile in the My Apps, this option redirects to FileCloud Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure FileCloud you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
