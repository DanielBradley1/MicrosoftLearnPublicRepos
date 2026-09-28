<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/gulfhr-sso-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure gulfHR SSO for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate gulfHR SSO with Microsoft Entra ID. When you integrate gulfHR SSO with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to gulfHR SSO.
- Enable your users to be automatically signed-in to gulfHR SSO with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- gulfHR SSO single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- gulfHR SSO supports only **IDP** initiated SSO.

## Add gulfHR SSO from the gallery

To configure the integration of gulfHR SSO into Microsoft Entra ID, you need to add gulfHR SSO from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **gulfHR SSO** in the search box.
4. Select **gulfHR SSO** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for gulfHR SSO

Configure and test Microsoft Entra SSO with gulfHR SSO using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in gulfHR SSO.

To configure and test Microsoft Entra SSO with gulfHR SSO, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure gulfHR SSO](#configure-gulfhr-sso)** - to configure the single sign-on settings on application side.

   1. **[Create gulfHR SSO test user](#create-gulfhr-sso-test-user)** - to have a counterpart of B.Simon in gulfHR SSO that's linked to the Microsoft Entra ID representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **gulfHR SSO** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://<GULFHR_CUSTOMER_SPECIFIC_DOMAIN>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<GULFHR_CUSTOMER_SPECIFIC_DOMAIN>/Security/Logon2.aspx`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [gulfHR SSO Client support team](mailto:helpdesk@gulfhr.ae) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.
6. In the **SAML Signing Certificate** section, select **Edit** button to open **SAML Signing Certificate** dialog.

   ![Screenshot shows to edit SAML Signing Certificate.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-certificate.png)

7. In the **SAML Signing Certificate** section, copy the **Thumbprint Value** and save it on your computer.

   ![Screenshot shows to copy Thumbprint value.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-thumbprint.png)

8. On the **Set up gulfHR SSO** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration URLs.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create a Microsoft Entra test user

In this section, you create a test user in the Microsoft Entra admin center called B.Simon.

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

In this section, you enable B.Simon to use Microsoft Entra single sign-on by granting access to gulfHR SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **gulfHR SSO**.
3. In the app's overview page, select **Users and groups**.
4. Select **Add user/group**, then select **Users and groups** in the **Add Assignment** dialog.

   1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
   2. If you're expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
   3. In the **Add Assignment** dialog, select the **Assign** button.

## Configure gulfHR SSO

To configure single sign-on on **gulfHR SSO** side, you need to send the **Thumbprint Value** and appropriate copied URLs from Microsoft Entra admin center to [gulfHR SSO support team](mailto:helpdesk@gulfhr.ae). They set this setting to have the SAML SSO connection set properly on both sides.

### Create gulfHR SSO test user

In this section, you create a user called B.Simon in gulfHR SSO. Work with [gulfHR SSO support team](mailto:helpdesk@gulfhr.ae) to add the users in the gulfHR SSO platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select Test this application in Microsoft Entra admin center and you should be automatically signed in to the gulfHR SSO for which you set up the SSO.
- You can use Microsoft My Apps. When you select the gulfHR SSO tile in the My Apps, you should be automatically signed in to the gulfHR SSO for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure gulfHR SSO you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
