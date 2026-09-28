<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/new-relic-limited-release-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-09 -->

# Configure New Relic for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate New Relic with Microsoft Entra ID. When you integrate New Relic with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to New Relic.
- Enable your users to be automatically signed-in to New Relic with their Microsoft Entra accounts.
- Manage your accounts in one central location: the Azure portal.

New Relic is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A New Relic organization on the [New Relic One account/user model](https://docs.newrelic.com/docs/accounts/accounts-billing/new-relic-one-user-management/introduction-managing-users/#user-models) and on either Pro or Enterprise edition. For more information, see [New Relic requirements](https://docs.newrelic.com/docs/accounts/accounts-billing/new-relic-one-user-management/authentication-domains-saml-sso-scim-more).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- New Relic supports SSO that's initiated by either the service provider or the identity provider.
- New Relic supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/new-relic-by-organization-provisioning-tutorial).

## Add New Relic from the gallery

To configure the integration of New Relic into Microsoft Entra ID, you need to add **New Relic \(By Organization\)** from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. On the **Browse Microsoft Entra Gallery** page, type **New Relic \(By Organization\)** in the search box.
4. Select **New Relic \(By Organization\)** from the results, and then select **Create**. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for New Relic

Configure and test Microsoft Entra SSO with New Relic by using a test user called **B.Simon**. For SSO to work, you need to establish a linked relationship between a Microsoft Entra user and the related user in New Relic.

To configure and test Microsoft Entra SSO with New Relic:

1. [Configure Microsoft Entra SSO](#configure-azure-ad-sso) to enable your users to use this feature.

   1. Create a Microsoft Entra test user to test Microsoft Entra single sign-on with B.Simon.
   2. Assign the Microsoft Entra test user to enable B.Simon to use Microsoft Entra single sign-on.

2. [Configure New Relic SSO](#configure-new-relic-sso) to configure the single sign-on settings on the New Relic side.

   1. [Create a New Relic test user](#create-a-new-relic-test-user) to have a counterpart for B.Simon in New Relic linked to the Microsoft Entra user.

3. [Test SSO](#test-sso) to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New Relic by Organization** application integration page, find the **Manage** section. Then select **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up Single Sign-On with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot of Set up Single Sign-On with SAML, with pencil icon highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, fill in values for **Identifier** and **Reply URL**.

   - Retrieve these values from the [New Relic authentication domain UI](https://docs.newrelic.com/docs/accounts/accounts-billing/new-relic-one-user-management/authentication-domains-saml-sso-scim-more/#ui). From there:

     1. If you have more than one authentication domain, choose the one to which you want Microsoft Entra SSO to connect. Most companies only have one authentication domain called **Default**. If there's only one authentication domain, you don't need to select anything.
     2. In the **Authentication** section, **Assertion consumer URL** contains the value to use for **Reply URL**.
     3. In the **Authentication** section, **Our entity ID** contains the value to use for **Identifier**.

6. In the **User Attributes & Claims** section, make sure **Unique User Identifier** is mapped to a field that contains the email address being used at New Relic.

   - The default field **user.userprincipalname** will work for you if its values are the same as the New Relic email addresses.
   - The field **user.mail** might work better for you if **user.userprincipalname** isn't the New Relic email address.

7. In the **SAML Signing Certificate** section, copy **App Federation Metadata Url** and save its value for later use.
8. In the **Set up New Relic by Organization** section, copy **Login URL** and save its value for later use.

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure New Relic SSO

Follow these steps to configure SSO at New Relic.

1. [Sign in](https://login.newrelic.com/) to New Relic.
2. Go to the [authentication domain UI](https://docs.newrelic.com/docs/accounts/accounts-billing/new-relic-one-user-management/authentication-domains-saml-sso-scim-more/#ui).
3. Choose the authentication domain to which you want Microsoft Entra SSO to connect \(if you have more than one authentication domain\). Most companies only have one authentication domain called **Default**. If there's only one authentication domain, you don't need to select anything.
4. In the **Authentication** section, select **Configure**.

   1. For **Source of SAML metadata**, enter the value you previously saved from the Microsoft Entra ID **App Federation Metadata Url** field.
   2. For **SSO target URL**, enter the value you previously saved from the Microsoft Entra ID **Login URL** field.
   3. After verifying that settings look good on both the Microsoft Entra ID and New Relic sides, select **Save**. If both sides aren't properly configured, your users won't be able to sign in to New Relic.

### Create a New Relic test user

In this section, you create a user called B.Simon in New Relic.

1. [Sign in](https://login.newrelic.com/) to New Relic.
2. Go to the [**User management** UI](https://docs.newrelic.com/docs/accounts/accounts-billing/new-relic-one-user-management/add-manage-users-groups-roles/#where).
3. Select **Add user**.

   1. For **Name**, enter **B.Simon**.
   2. For **Email**, enter the value that's sent by Microsoft Entra SSO.
   3. Choose a user **Type** and a user **Group** for the user. For a test user, **Basic user** for Type and **User** for Group are reasonable choices.
   4. To save the user, select **Add User**.

Note

New Relic also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/new-relic-by-organization-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to New Relic Sign on URL where you can initiate the login flow.
- Go to New Relic Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the New Relic for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the New Relic tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the New Relic for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once done, you can verify that your users have been added in New Relic by going to the [**User management** UI](https://docs.newrelic.com/docs/accounts/accounts-billing/new-relic-one-user-management/add-manage-users-groups-roles/#where) and seeing if they're there.

Next, you probably want to assign your users to specific New Relic accounts or roles. To learn more about this, see [User management concepts](https://docs.newrelic.com/docs/accounts/accounts-billing/new-relic-one-user-management/add-manage-users-groups-roles/#understand-concepts).

In New Relic's authentication domain UI, you can configure [other settings](https://docs.newrelic.com/docs/accounts/accounts-billing/new-relic-one-user-management/authentication-domains-saml-sso-scim-more/#session-mgmt), like session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
