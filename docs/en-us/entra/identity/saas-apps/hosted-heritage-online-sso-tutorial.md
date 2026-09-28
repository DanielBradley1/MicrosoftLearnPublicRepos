<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/hosted-heritage-online-sso-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Hosted Heritage Online SSO for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Hosted Heritage Online SSO with Microsoft Entra ID. When you integrate Hosted Heritage Online SSO with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Hosted Heritage Online SSO.
- Enable your users to be automatically signed-in to Hosted Heritage Online SSO with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Hosted Heritage Online SSO single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Hosted Heritage Online SSO supports **SP** initiated SSO.

## Add Hosted Heritage Online SSO from the gallery

To configure the integration of Hosted Heritage Online SSO into Microsoft Entra ID, you need to add Hosted Heritage Online SSO from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Hosted Heritage Online SSO** in the search box.
4. Select **Hosted Heritage Online SSO** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Hosted Heritage Online SSO

Configure and test Microsoft Entra SSO with Hosted Heritage Online SSO using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Hosted Heritage Online SSO.

To configure and test Microsoft Entra SSO with Hosted Heritage Online SSO, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Hosted Heritage Online SSO SSO](#configure-hosted-heritage-online-sso-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Hosted Heritage Online SSO test user](#create-hosted-heritage-online-sso-test-user)** - to have a counterpart of B.Simon in Hosted Heritage Online SSO that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Hosted Heritage Online SSO** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.cirqahosting.com/shibboleth`

   b. In the **Sign on URL** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.cirqahosting.com/Shibboleth.sso/Login`

   Note

   These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [Hosted Heritage Online SSO Client support team](mailto:support@isoxford.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create a Microsoft Entra test user

In this section, you create a test user called B.Simon.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Users**.
3. Select **New user** > **Create new user**, at the top of the screen.
4. In the **User** properties, follow these steps:

   1. In the **Display name** field, enter `B.Simon`.
   2. In the **User principal name** field, enter the username@companydomain.extension. For example, `B.Simon@contoso.com`.
   3. Select the **Show password** check box, and then write down the value that's displayed in the **Password** box.
   4. Select **Review + create**.

5. Select **Create**.

### Assign the Microsoft Entra test user

In this section, you enable B.Simon to use single sign-on by granting access to Hosted Heritage Online SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Hosted Heritage Online SSO**.
3. In the app's overview page, find the **Manage** section and select **Users and groups**.
4. Select **Add user**, then select **Users and groups** in the **Add Assignment** dialog.
5. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
6. If you're expecting any role value in the SAML assertion, in the **Select Role** dialog, select the appropriate role for the user from the list and then select the **Select** button at the bottom of the screen.
7. In the **Add Assignment** dialog, select the **Assign** button.

## Configure Hosted Heritage Online SSO SSO

To configure single sign-on on **Hosted Heritage Online SSO** side, you need to send the **App Federation Metadata Url** to [Hosted Heritage Online SSO support team](mailto:support@isoxford.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Hosted Heritage Online SSO test user

In this section, you create a user called B.Simon in Hosted Heritage Online SSO. Work with [Hosted Heritage Online SSO support team](mailto:support@isoxford.com) to add the users in the Hosted Heritage Online SSO platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Hosted Heritage Online SSO Sign-on URL where you can initiate the login flow.
- Go to Hosted Heritage Online SSO Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Hosted Heritage Online SSO tile in the My Apps, this option redirects to Hosted Heritage Online SSO Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Hosted Heritage Online SSO you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
