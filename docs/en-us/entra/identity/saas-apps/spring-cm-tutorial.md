<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/spring-cm-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure SpringCM for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate SpringCM with Microsoft Entra ID. When you integrate SpringCM with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to SpringCM.
- Enable your users to be automatically signed-in to SpringCM with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- SpringCM single sign-on enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- SpringCM supports **SP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add SpringCM from the gallery

To configure the integration of SpringCM into Microsoft Entra ID, you need to add SpringCM from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **SpringCM** in the search box.
4. Select **SpringCM** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for SpringCM

Configure and test Microsoft Entra SSO with SpringCM using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in SpringCM.

To configure and test Microsoft Entra SSO with SpringCM, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure SpringCM SSO](#configure-springcm-sso)** - to configure the single sign-on settings on application side.

   1. **[Create SpringCM test user](#create-springcm-test-user)** - to have a counterpart of B.Simon in SpringCM that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **SpringCM** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://na11.springcm.com/atlas/SSO/SSOEndpoint.ashx?aid=<IDENTIFIER>`

   Note

   The value isn't real. Update the value with the actual Sign-On URL. Contact [SpringCM Client support team](https://support.docusign.com/s/) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Raw\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificateraw.png)

7. On the **Set up SpringCM** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure SpringCM SSO

1. In a different web browser window, sign on to your **SpringCM** company site as administrator.
2. In the menu on the top, select **GO TO**, select **Preferences**, and then, in the **Account Preferences** section, select **SAML SSO**.

   ![SAML SSO](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/spring-cm-tutorial/preferences.png "SAML SSO")

3. In the Identity Provider Configuration section, perform the following steps:

   ![Identity Provider Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/spring-cm-tutorial/configuration.png "Identity Provider Configuration")


   a. To upload your downloaded Microsoft Entra certificate, select **Select Issuer Certificate** or **Change Issuer Certificate**.


   b. In the **Issuer** textbox, paste **Microsoft Entra Identifier** value.


   c. In the **Service Provider \(SP\) Initiated Endpoint** textbox, paste **Login URL** value, which you copied previously.


   d. Select **SAML Enabled** as **Enable**.


   e. Select **Save**.

### Create SpringCM test user

To enable Microsoft Entra users to sign in to SpringCM, they must be provisioned into SpringCM. In the case of SpringCM, provisioning is a manual task.

Note

For more information, see [Create and Edit a SpringCM User](https://support.docusign.com/s/document-item?language=en_US&bundleId=fsk1642969066834&topicId=ynn1576609925288.html&_LANG=enus).

**To provision a user account to SpringCM, perform the following steps:**

1. Sign in to your **SpringCM** company site as administrator.
2. Select **GOTO**, and then select **ADDRESS BOOK**.

   ![Create User](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/spring-cm-tutorial/user.png "Create User")

3. Select **Create User**.
4. Select a **User Role**.
5. Select **Send Activation Email**.
6. Type the first name, last name, and email address of a valid Microsoft Entra user account you want to provision into the related textboxes.
7. Add the user to a **Security group**.
8. Select **Save**.

   Note

   You can use any other SpringCM user account creation tools or APIs provided by SpringCM to provision Microsoft Entra user accounts.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to SpringCM Sign-on URL where you can initiate the login flow.
- Go to SpringCM Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the SpringCM tile in the My Apps, this option redirects to SpringCM Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure SpringCM you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
