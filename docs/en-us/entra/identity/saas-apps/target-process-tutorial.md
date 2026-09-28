<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/target-process-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure TargetProcess for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate TargetProcess with Microsoft Entra ID. When you integrate TargetProcess with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to TargetProcess.
- Enable your users to be automatically signed-in to TargetProcess with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- TargetProcess single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- TargetProcess supports **SP** initiated SSO.
- TargetProcess supports **Just In Time** user provisioning.

## Add TargetProcess from the gallery

To configure the integration of TargetProcess into Microsoft Entra ID, you need to add TargetProcess from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **TargetProcess** in the search box.
4. Select **TargetProcess** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for TargetProcess

Configure and test Microsoft Entra SSO with TargetProcess using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in TargetProcess.

To configure and test Microsoft Entra SSO with TargetProcess, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure TargetProcess SSO](#configure-targetprocess-sso)** - to configure the single sign-on settings on application side.

   1. **[Create TargetProcess test user](#create-targetprocess-test-user)** - to have a counterpart of B.Simon in TargetProcess that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **TargetProcess** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.tpondemand.com/`

   b. In the **Sign on URL** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.tpondemand.com/`

   Note

   These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [TargetProcess Client support team](mailto:support@targetprocess.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up TargetProcess** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure TargetProcess SSO

1. Sign-on to your TargetProcess application as an administrator.
2. In the menu on the top, select **Setup**.

   ![Setup](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/target-process-tutorial/menu.png)

3. Select **Settings** tab.

   ![Settings](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/target-process-tutorial/profile.png)

4. Select **Single Sign-on** tab.

   ![select Single Sign-On](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/target-process-tutorial/personal-settings.png)

5. On the Single Sign-on settings dialog, perform the following steps:

   ![Configure Single Sign-On](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/target-process-tutorial/certificate.png)


   a. Select **Enable Single Sign-on**.


   b. In **Sign-on URL** textbox, paste the value of **Login URL**..


   c. Open your downloaded certificate in notepad, copy the content, and then paste it into the **Certificate** textbox.


   d. select **Enable JIT Provisioning**.


   e. Select **Save**.

### Create TargetProcess test user

In this section, a user called Britta Simon is created in TargetProcess. TargetProcess supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in TargetProcess, a new one is created after authentication.

Note

If you need to create a user manually, contact [TargetProcess support team](mailto:support@targetprocess.com).

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to TargetProcess Sign-on URL where you can initiate the login flow.
- Go to TargetProcess Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the TargetProcess tile in the My Apps, this option redirects to TargetProcess Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure TargetProcess you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
