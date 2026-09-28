<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/hive-learning-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Hive Learning for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Hive Learning with Microsoft Entra ID. When you integrate Hive Learning with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Hive Learning.
- Enable your users to be automatically signed-in to Hive Learning with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Hive Learning single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Hive Learning supports **SP** and **IDP** initiated SSO.
- Hive Learning supports **Just In Time** user provisioning.

## Add Hive Learning from the gallery

To configure the integration of Hive Learning into Microsoft Entra ID, you need to add Hive Learning from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Hive Learning** in the search box.
4. Select **Hive Learning** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Hive Learning

Configure and test Microsoft Entra SSO with Hive Learning using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Hive Learning.

To configure and test Microsoft Entra SSO with Hive Learning, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Hive Learning SSO](#configure-hive-learning-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Hive Learning test user](#create-hive-learning-test-user)** - to have a counterpart of B.Simon in Hive Learning that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Hive Learning** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type a URL using the following pattern: `https://auth.hivelearning.com/saml/<ID>/metadata`

   b. In the **Reply URL** textbox, type a URL using the following pattern: `https://auth.hivelearning.com/saml/<ID>/login`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign on URL** text box, type a URL using the following pattern: `https://<ID>.hivelearning.com`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [Hive Learning support team](mailto:help@hivelearning.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

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

In this section, you enable B.Simon to use single sign-on by granting access to Hive Learning.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Hive Learning**.
3. In the app's overview page, select **Users and groups**.
4. Select **Add user/group**, then select **Users and groups** in the **Add Assignment** dialog.

   1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
   2. If you're expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
   3. In the **Add Assignment** dialog, select the **Assign** button.

## Configure Hive Learning SSO

To configure single sign-on on **Hive Learning** side, you need to send the **App Federation Metadata Url** to [Hive Learning support team](mailto:help@hivelearning.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Hive Learning test user

In this section, a user called B.Simon is created in Hive Learning. Hive Learning supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Hive Learning, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Hive Learning Sign on URL where you can initiate the login flow.
- Go to Hive Learning Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Hive Learning for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Hive Learning tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Hive Learning for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Hive Learning you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
