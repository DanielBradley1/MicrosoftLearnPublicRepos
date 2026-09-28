<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/asana-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Asana for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Asana with Microsoft Entra ID. When you integrate Asana with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Asana.
- Enable your users to be automatically signed-in to Asana with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Asana single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Asana supports **SP** initiated SSO.
- Asana supports [**automated** user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/asana-provisioning-tutorial).

## Add Asana from the gallery

To configure the integration of Asana into Microsoft Entra ID, you need to add Asana from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Asana** in the search box.
4. Select **Asana** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Asana

Configure and test Microsoft Entra SSO with Asana using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Asana.

To configure and test Microsoft Entra SSO with Asana, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Asana SSO](#configure-asana-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Asana test user](#create-asana-test-user)** - to have a counterpart of B.Simon in Asana that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Asana** application integration page, find the **Manage** section and select **Single sign-on**.
3. On the **Select a Single sign-on method** page, select **SAML**.
4. On the **Set up Single Sign-On with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type the URL: `https://app.asana.com/`

   Note

   If you require a different value to the Identifier \(Entity ID\) please [get in touch with us](https://form-beta.asana.com/?k=BT9rHN4rEoRKARjEYg6neA&d=15793206719).

   b. In the **Reply URL \(Assertion Consumer Service URL\)** text box, type the URL: `https://app.asana.com/-/saml/consume`

   c. In the **Sign on URL** text box, type the URL: `https://app.asana.com/a/<email_suffix>`

   Note

   If you own many email domains, feel free to use any one of them.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png "Certificate")

7. On the **Set up Asana** section, copy the appropriate URL\(s\) as per your requirement.

   ![Screenshot shows to copy configuration appropriate URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

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

In this section, you enable B.Simon to use single sign-on by granting access to Asana.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Asana**.
3. In the app's overview page, select **Users and groups**.
4. Select **Add user/group**, then select **Users and groups** in the **Add Assignment** dialog.

   1. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
   2. If you're expecting a role to be assigned to the users, you can select it from the **Select a role** dropdown. If no role has been set up for this app, you see "Default Access" role selected.
   3. In the **Add Assignment** dialog, select the **Assign** button.

### Configure Asana SSO

1. In a different browser window, sign on to your Asana application. To configure SSO in Asana, access the admin console by selecting the avatar on the top right corner of the screen. Then, select **Admin Console**.

   ![Screenshot showing Asana admin console settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/asana-tutorial/settings.png)

2. Navigate to the **Security** tab. Then select **SAML Authentication**.

   ![Screenshot showing Configure Single Sign-On Organization settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/asana-tutorial/save.png)

3. Perform the following steps in the below page:

   ![Screenshot showing Configure Single Sign-On SAML Authentication settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/asana-tutorial/authentication.png)


   a. Select Required for all members, except guest accounts.


   b. Paste the **sign-in URL** that you into its **sign-in page URL** textbox. c. Paste the **Certificate \(Base64\)** content that you into **X.509 Certificate** field. d. Set the session duration for your members. e. Select **Save**.

Note

Go to Asana [guide](https://asana.com/guide/help/premium/authentication#gl-saml) for setting up SSO if you need further assistance.

### Create Asana test user

The objective of this section is to create a user called Britta Simon in Asana. Asana supports automatic user provisioning, which is by default enabled. You can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/asana-provisioning-tutorial) on how to configure automatic user provisioning.

**If you need to create user manually, please perform following steps:**

In this section, you create a user called Britta Simon in Asana.

1. On **Asana**, go to the **Teams** section on the left panel. Select the plus sign button.

   ![Screenshot showing Creating a Microsoft Entra test user.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/asana-tutorial/teams.png)

2. Type the email of the user like **britta.simon@contoso.com** in the text box and then select **Invite**.
3. Select **Send Invite**. The new user receives an email into their email account. user needs to create and validate the account.

### Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Asana Sign-on URL where you can initiate the login flow.
- Go to Asana Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Asana tile in the My Apps, this option redirects to Asana Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Asana you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
