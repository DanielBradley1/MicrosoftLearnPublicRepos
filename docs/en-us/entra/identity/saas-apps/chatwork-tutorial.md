<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/chatwork-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Chatwork for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Chatwork with Microsoft Entra ID. When you integrate Chatwork with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Chatwork.
- Enable your users to be automatically signed-in to Chatwork with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Chatwork single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Chatwork supports **SP** initiated SSO.
- Chatwork supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/chatwork-provisioning-tutorial).

## Adding Chatwork from the gallery

To configure the integration of Chatwork into Microsoft Entra ID, you need to add Chatwork from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Chatwork** in the search box.
4. Select **Chatwork** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Chatwork

Configure and test Microsoft Entra SSO with Chatwork using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Chatwork.

To configure and test Microsoft Entra SSO with Chatwork, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Chatwork SSO](#configure-chatwork-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Chatwork test user](#create-chatwork-test-user)** - to have a counterpart of B.Simon in Chatwork that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Chatwork** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following step:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://www.chatwork.com/s/<TENANT_NAME>`

   Note

   The value isn't real. Update the value with the private login URL which you set after **Chatwork SSO configuration**.
6. Chatwork application expects the value of **Unique User Identifier** attribute matches the email address registered in Chatwork. The attribute is mapped to **user.principalname** by default. If the principalname is different from the email address, map **Unique User Identifier** to **user.mail**.
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

8. On the **Set up Chatwork** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Chatwork SSO

To configure single sign-on on **Chatwork** side, please read the [Chatwork Admin Guide](https://download.chatwork.com/Chatwork_AdminGuide.pdf) and configure a Chatwork setting.

### Create Chatwork test user

In this section, you create a user called B.Simon in Chatwork. Access the [Chatwork Admin Guide](https://download.chatwork.com/Chatwork_AdminGuide.pdf) and add the user in the Chatwork platform.

Chatwork also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/chatwork-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Chatwork Sign-on URL where you can initiate the login flow.
- Go to Chatwork Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Chatwork tile in the My Apps, this option redirects to Chatwork Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Chatwork you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
