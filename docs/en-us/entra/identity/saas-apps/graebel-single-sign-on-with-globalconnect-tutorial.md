<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/graebel-single-sign-on-with-globalconnect-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-11 -->

# Configure Graebel Single Sign On with globalCONNECT for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Graebel Single Sign On with globalCONNECT with Microsoft Entra ID. When you integrate Graebel Single Sign On with globalCONNECT with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Graebel Single Sign On with globalCONNECT.
- Enable your users to be automatically signed-in to Graebel Single Sign On with globalCONNECT with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Graebel Single Sign On with globalCONNECT single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Graebel Single Sign On with globalCONNECT supports both **SP and IDP** initiated SSO.
- Graebel Single Sign On with globalCONNECT supports **Just In Time** user provisioning.

## Add Graebel Single Sign On with globalCONNECT from the gallery

To configure the integration of Graebel Single Sign On with globalCONNECT into Microsoft Entra ID, you need to add Graebel Single Sign On with globalCONNECT from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Graebel Single Sign On with globalCONNECT** in the search box.
4. Select **Graebel Single Sign On with globalCONNECT** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Graebel Single Sign On with globalCONNECT

Configure and test Microsoft Entra SSO with Graebel Single Sign On with globalCONNECT using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Graebel Single Sign On with globalCONNECT.

To configure and test Microsoft Entra SSO with Graebel Single Sign On with globalCONNECT, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-microsoft-entra-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Create a Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Graebel Single Sign On with globalCONNECT SSO](#configure-graebel-single-sign-on-with-globalconnect-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Graebel Single Sign On with globalCONNECT test user](#create-graebel-single-sign-on-with-globalconnect-test-user)** - to have a counterpart of B.Simon in Graebel Single Sign On with globalCONNECT that's linked to the Microsoft Entra ID representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Microsoft Entra admin center.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Graebel Single Sign On with globalCONNECT** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://<CUSTOMER_NAME>.graebel.com/custom/sso/so.aspx`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<CUSTOMER_NAME>.graebel.com/custom/sso/so.aspx`
6. Perform the following step, if you wish to configure the application in **SP** initiated mode:

   In the **Sign on URL** text box, type a URL using the following pattern: `https://<CUSTOMER_NAME>.graebel.com/custom/sso/so.aspx`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [Graebel Single Sign On with globalCONNECT support team](mailto:filetransfer@graebel.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section in the Microsoft Entra admin center.
7. Graebel Single Sign On with globalCONNECT application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Image")

8. In addition to above, Graebel Single Sign On with globalCONNECT application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | SAML\_SUBJECT | user.mail |
9. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

10. On the **Set up Graebel Single Sign On with globalCONNECT** section, copy the appropriate URL\(s\) based on your requirement.

    ![Screenshot shows to copy configuration URLs.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create a Microsoft Entra ID test user

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

### Assign the Microsoft Entra ID test user

In this section, you enable B.Simon to use Microsoft Entra single sign-on by granting access to Graebel Single Sign On with globalCONNECT.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Graebel Single Sign On with globalCONNECT**.
3. In the app's overview page, select **Users and groups**.
4. Select **Add user/group**, then select **Users and groups** in the **Add Assignment** dialog.

   1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
   2. If you're expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
   3. In the **Add Assignment** dialog, select the **Assign** button.

## Configure Graebel Single Sign On with globalCONNECT SSO

To configure single sign-on on **Graebel Single Sign On with globalCONNECT** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from Microsoft Entra admin center to [Graebel Single Sign On with globalCONNECT support team](mailto:filetransfer@graebel.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Graebel Single Sign On with globalCONNECT test user

In this section, a user called Britta Simon is created in Graebel Single Sign On with globalCONNECT. Graebel Single Sign On with globalCONNECT supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Graebel Single Sign On with globalCONNECT, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application** in Microsoft Entra admin center. this option redirects to Graebel Single Sign On with globalCONNECT Sign-on URL where you can initiate the login flow.
- Go to Graebel Single Sign On with globalCONNECT Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application** in Microsoft Entra admin center and you should be automatically signed in to the Graebel Single Sign On with globalCONNECT for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Graebel Single Sign On with globalCONNECT tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Graebel Single Sign On with globalCONNECT for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Graebel Single Sign On with globalCONNECT you can enforce session control, which protects exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
