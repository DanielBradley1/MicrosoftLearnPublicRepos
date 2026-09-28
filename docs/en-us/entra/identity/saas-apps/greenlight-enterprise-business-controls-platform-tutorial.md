<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/greenlight-enterprise-business-controls-platform-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Greenlight Enterprise Business Controls Platform for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Greenlight Enterprise Business Controls Platform with Microsoft Entra ID. When you integrate Greenlight Enterprise Business Controls Platform with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Greenlight Enterprise Business Controls Platform.
- Enable your users to be automatically signed-in to Greenlight Enterprise Business Controls Platform with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Greenlight Enterprise Business Controls Platform single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Greenlight Enterprise Business Controls Platform supports **SP and IDP** initiated SSO.

## Add Greenlight Enterprise Business Controls Platform from the gallery

To configure the integration of Greenlight Enterprise Business Controls Platform into Microsoft Entra ID, you need to add Greenlight Enterprise Business Controls Platform from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Greenlight Enterprise Business Controls Platform** in the search box.
4. Select **Greenlight Enterprise Business Controls Platform** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Greenlight Enterprise Business Controls Platform

Configure and test Microsoft Entra SSO with Greenlight Enterprise Business Controls Platform using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Greenlight Enterprise Business Controls Platform.

To configure and test Microsoft Entra SSO with Greenlight Enterprise Business Controls Platform, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Greenlight Enterprise Business Controls Platform SSO](#configure-greenlight-enterprise-business-controls-platform-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Greenlight Enterprise Business Controls Platform test user](#create-greenlight-enterprise-business-controls-platform-test-user)** - to have a counterpart of B.Simon in Greenlight Enterprise Business Controls Platform that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Greenlight Enterprise Business Controls Platform** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://<CUSTOMER_NAME>.gltcloud.com/ebcpplatform/saml`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<CUSTOMER_NAME>.gltcloud.com/ebcpplatform/saml`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://<CUSTOMER_NAME>.gltcloud.com/ebcpplatform/saml`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-on URL. Contact [Greenlight Enterprise Business Controls Platform Client support team](mailto:support@greenlightcorp.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

8. On the **Set up Greenlight Enterprise Business Controls Platform** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

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

In this section, you enable B.Simon to use single sign-on by granting access to Greenlight Enterprise Business Controls Platform.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Greenlight Enterprise Business Controls Platform**.
3. In the app's overview page, find the **Manage** section and select **Users and groups**.
4. Select **Add user**, then select **Users and groups** in the **Add Assignment** dialog.
5. In the **Users and groups** dialog, select **B.Simon** from the Users list, then select the **Select** button at the bottom of the screen.
6. If you're expecting any role value in the SAML assertion, in the **Select Role** dialog, select the appropriate role for the user from the list and then select the **Select** button at the bottom of the screen.
7. In the **Add Assignment** dialog, select the **Assign** button.

## Configure Greenlight Enterprise Business Controls Platform SSO

To configure single sign-on on **Greenlight Enterprise Business Controls Platform** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Greenlight Enterprise Business Controls Platform support team](mailto:support@greenlightcorp.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Greenlight Enterprise Business Controls Platform test user

In this section, you create a user called B.Simon in Greenlight Enterprise Business Controls Platform. Work with [Greenlight Enterprise Business Controls Platform support team](mailto:support@greenlightcorp.com) to add the users in the Greenlight Enterprise Business Controls Platform platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Greenlight Enterprise Business Controls Platform Sign on URL where you can initiate the login flow.
- Go to Greenlight Enterprise Business Controls Platform Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Greenlight Enterprise Business Controls Platform for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Greenlight Enterprise Business Controls Platform tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Greenlight Enterprise Business Controls Platform for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Greenlight Enterprise Business Controls Platform you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
