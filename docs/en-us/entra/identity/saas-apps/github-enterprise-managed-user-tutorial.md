<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-enterprise-managed-user-tutorial -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Configure a GitHub enterprise with Enterprise Managed Users for SAML Single sign-on with Microsoft Entra ID

In this article, you learn how to set up a SAML integration for a GitHub enterprise with Enterprise Managed Users with Microsoft Entra ID. Setting up a SAML or [OIDC](https://docs.github.com/enterprise-cloud@latest/admin/managing-iam/configuring-authentication-for-enterprise-managed-users/configuring-oidc-for-enterprise-managed-users) authentication integration, in addition to setting up [SCIM provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-enterprise-managed-user-provisioning-tutorial), is required for a GitHub enterprise with Enterprise Managed Users. Setting up authentication and [SCIM provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-enterprise-managed-user-provisioning-tutorial) for a GitHub enterprise with Enterprise Managed Users allows an admin to:

- Control in Microsoft Entra ID who has access to a GitHub enterprise with Enterprise Managed Users.
- Enable your users to log into a GitHub Enterprise Managed User account via SSO.
- Provision users and groups to the enterprise \(once both the authentication and SCIM provisioning integrations have been set up\). GitHub teams can be mapped to SCIM-provisioned groups.
- Manage your accounts and groups in one central location, Entra ID.

Note

A GitHub.com enterprise account with Enterprise Managed Users is a specific type of enterprise. This is determined with you request or [create a new GitHub enterprise account](https://docs.github.com/en/enterprise-cloud@latest/admin/managing-your-enterprise-account/creating-an-enterprise-account) on GitHub.com. You can read more about the different types of GitHub enterprises in [this GitHub article](https://docs.github.com/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/choosing-an-enterprise-type-for-github-enterprise-cloud). If you do not have an enterprise that is set up for Enterprise Managed Users, please see [this GitHub article](https://docs.github.com/en/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/about-identity-and-access-management#authentication-through-githubcom-with-additional-saml-access-restriction) for more details and links.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- GitHub Enterprise Managed User single sign-on \(SSO\) enabled subscription.
- A GitHub enterprise that is set up for Enterprise Managed Users.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- GitHub Enterprise Managed User supports both **SP and IDP** initiated SSO.
- GitHub Enterprise Managed User requires [**Automated** user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-enterprise-managed-user-provisioning-tutorial).

Note

The GitHub `Enterprise Managed User` application currently doesn't support any of the government cloud platforms.

## Adding GitHub Enterprise Managed User from the gallery

To configure the integration of GitHub Enterprise Managed User into Microsoft Entra ID, you need to add GitHub Enterprise Managed User from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. Type **GitHub Enterprise Managed User** in the search box.
4. Select **GitHub Enterprise Managed User** from results panel and then select the **Create** button. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SAML SSO for a GitHub enterprise with Enterprise Managed Users

To configure and test Microsoft Entra SSO with GitHub Enterprise Managed User, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable SAML Single Sign On in your Microsoft Entra tenant.
2. **[Configure GitHub Enterprise Managed User SSO](#configure-github-enterprise-managed-user-sso)** - to configure the single sign-on settings in your GitHub Enterprise.

## Configure Microsoft Entra SAML SSO

Follow these steps to enable Microsoft Entra SAML SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **GitHub Enterprise Managed User** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. Ensure that you have your Enterprise URL before you begin. The ENTITY field mentioned below is the Enterprise name of your EMU-enabled Enterprise URL. For example, [https://github.com/enterprises/contoso](https://github.com/enterprises/contoso) - **contoso** is the ENTITY. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, enter the values for the following fields:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://github.com/enterprises/{enterprise}`

   Note

   Note the identifier format is different from the application's suggested format - please follow the format above. In addition, please ensure the \*\*Identifier doesn't contain a trailing slash.

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://github.com/enterprises/{enterprise}/saml/consume`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://github.com/enterprises/{enterprise}/sso`
7. On the **Set up single sign-on with SAML** page, in the **SAML Certificates** section, download the Base64 certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificate-base64.png "Certificate")

8. On the **Set up GitHub Enterprise Managed User** section, copy the URLs below and save it for configuring GitHub below.

   ![Screenshot shows to copy configuration URLs.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Assign the Microsoft Entra test user

In this section, you assign your account to GitHub Enterprise Managed User in order to complete SSO setup.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **GitHub Enterprise Managed User**.
3. In the app's overview page, find the **Manage** section and select **Users and groups**.
4. Select **Add user**, then select **Users and groups** in the **Add Assignment** dialog.
5. In the **Users and groups** dialog, select your account from the Users list, then select the **Select** button at the bottom of the screen.
6. In the **Select a role** dialog, select the **Enterprise Owner** role, then select the **Select** button at the bottom of the screen. Your account is assigned as an Enterprise Owner for your GitHub instance when you provision your account in the next article.
7. In the **Add Assignment** dialog, select the **Assign** button.

## Configure GitHub Enterprise Managed User SSO

To configure single sign-on on **GitHub Enterprise Managed User** side, you require the following items from the Entra ID app:

1. The URLs from your Microsoft Entra Enterprise Managed User Application above: the `Login URL` and the `Microsoft Entra Identifier`.
2. The downloaded base64 certificate.
3. The username and password for [the setup user account](https://docs.github.com/enterprise-cloud@latest/admin/managing-iam/understanding-iam-for-enterprises/getting-started-with-enterprise-managed-users#create-the-setup-user) for your GitHub enterprise.

### Enable GitHub Enterprise Managed User SAML SSO

In this section, you take the information provided from Microsoft Entra ID above and enter them into your Enterprise settings to enable SSO support.

1. Follow the steps in [this GitHub documentation](https://docs.github.com/enterprise-cloud@latest/admin/managing-iam/configuring-authentication-for-enterprise-managed-users/configuring-saml-single-sign-on-for-enterprise-managed-users#configure-your-enterprise) to configure SAML authentication for your enterprise.
2. When entering the `Sign-on URL`, note that this is the Login URL that you copied from Microsoft Entra ID above.
3. When entering the `Issuer`, note that this is the `Microsoft Entra Identifier` that you copied from Microsoft Entra ID above.
4. When entering the Public Certificate, open the base64 certificate that you downloaded above and paste the text contents of that file into this dialog.
5. After completing the steps in GitHub documentation to configure SAML authentication for your enterprise, only SCIM-provisioned enterprise managed users will be able to access the enterprise \(with the exception of logging in with the setup user account and using an enterprise recovery code\). Complete the steps in the Provisioning tutorial below to configure SCIM provisioning for the GitHub enterprise, so that you can provision Enterprise Managed Users and groups. Users will not be able to log in and access the enterprise until these steps are completed and their user accounts have been SCIM provisioned in the enterprise.

## Related content

GitHub Enterprise Managed User **requires** all accounts to be created through automatic \(SCIM\) user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/github-enterprise-managed-user-provisioning-tutorial) on how to configure automatic user provisioning.
