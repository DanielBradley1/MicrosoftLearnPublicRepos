<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/imagerelay-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Image Relay for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Image Relay with Microsoft Entra ID. When you integrate Image Relay with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Image Relay.
- Enable your users to be automatically signed-in to Image Relay with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Image Relay single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Image Relay supports **SP** initiated SSO.

## Add Image Relay from the gallery

To configure the integration of Image Relay into Microsoft Entra ID, you need to add Image Relay from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Image Relay** in the search box.
4. Select **Image Relay** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Image Relay

Configure and test Microsoft Entra SSO with Image Relay using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Image Relay.

To configure and test Microsoft Entra SSO with Image Relay, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Image Relay SSO](#configure-image-relay-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Image Relay test user](#create-image-relay-test-user)** - to have a counterpart of B.Simon in Image Relay that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Image Relay** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://<COMPANYNAME>.imagerelay.com/sso/metadata`

   b. In the **Sign on URL** text box, type a URL using the following pattern: `https://<COMPANYNAME>.imagerelay.com/`

   Note

   These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [Image Relay Client support team](http://support.imagerelay.com/) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up Image Relay** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Image Relay SSO

1. In another browser window, sign in to your Image Relay company site as an administrator.
2. In the toolbar on the top, select the **Users & Permissions** workload.

   ![Screenshot shows Users & Permissions selected from the toolbar.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/users.png)

3. Select **Create New Permission**.

   ![Screenshot shows a text box to enter Permission title and an option to choose Permission Type.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/create-permission.png)

4. In the **Single Sign On Settings** workload, select the **This Group can only sign-in via Single Sign On** check box, and then select **Save**.

   ![Screenshot shows the Single Sign On Settings where you can select the option.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/save-settings.png)

5. Go to **Account Settings**.

   ![Screenshot shows the Account Settings toolbar option.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/account.png)

6. Go to the **Single Sign On Settings** workload.

   ![Screenshot shows the Single Sign On Settings menu option.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/settings.png)

7. On the **SAML Settings** dialog, perform the following steps:

   ![Screenshot shows the SAML Settings dialog box where you can enter the information.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/information.png)


   a. In **Login URL** textbox, paste the value of **Login URL**..


   b. In **Logout URL** textbox, paste the value of **Logout URL**..


   c. As **Name Id Format**, select **urn:oasis:names:tc:SAML:1.1:nameid-format:emailAddress**.


   d. As **Binding Options for Requests from the Service Provider \(Image Relay\)**, select **POST Binding**.


   e. Under **x.509 Certificate**, select **Update Certificate**.


   ![Screenshot shows the option to Update Certificate.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/certificate.png)


   f. Open the downloaded certificate in notepad, copy the content, and then paste it into the **x.509 Certificate** textbox.


   ![Screenshot shows the x dot 509 Certificate.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/update-certificate.png)


   g. In **Just-In-Time User Provisioning** section, select the **Enable Just-In-Time User Provisioning**.


   ![Screenshot shows the Just-In-Time User Provisioning section with the enable control selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/provisioning.png)


   h. Select the permission group \(for example, **SSO Basic**\) which is allowed to sign in only through single sign-on.


   ![Screenshot shows the Just-In-Time User Provisioning section with S S O Basic selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/user-provisioning.png)


   i. Select **Save**.

### Create Image Relay test user

The objective of this section is to create a user called Britta Simon in Image Relay.

**To create a user called Britta Simon in Image Relay, perform the following steps:**

1. Sign-on to your Image Relay company site as an administrator.
2. Go to **Users & Permissions** and select **Create SSO User**.

   ![Screenshot shows Create S S O User selected from the menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/create-user.png)

3. Enter the **Email**, **First Name**, **Last Name**, and **Company** of the user you want to provision and select the permission group \(for example, SSO Basic\) which is the group that can sign in only through single sign-on.

   ![Screenshot shows Create a S S O User page where you can enter the required information.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/imagerelay-tutorial/user-details.png)

4. Select **Create**.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Image Relay Sign-on URL where you can initiate the login flow.
- Go to Image Relay Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Image Relay tile in the My Apps, this option redirects to Image Relay Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Image Relay you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
