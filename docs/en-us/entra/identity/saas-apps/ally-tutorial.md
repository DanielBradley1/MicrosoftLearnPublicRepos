<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/ally-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Ally.io for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Ally.io with Microsoft Entra ID. When you integrate Ally.io with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Ally.io.
- Enable your users to be automatically signed-in to Ally.io with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Ally.io single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Ally.io supports **SP and IDP** initiated SSO.
- Ally.io supports **Just In Time** user provisioning.

## Add Ally.io from the gallery

To configure the integration of Ally.io into Microsoft Entra ID, you need to add Ally.io from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Ally.io** in the search box.
4. Select **Ally.io** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Ally.io

Configure and test Microsoft Entra SSO with Ally.io using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Ally.io.

To configure and test Microsoft Entra SSO with Ally.io, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Ally.io SSO](#configure-allyio-sso)** - to configure the single sign-on settings on application side.
3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Ally.io** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, enter the values for the following fields:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://app.ally.io/saml/consume/<CUSTOM_GUID>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://app.ally.io/saml/consume/<CUSTOM_GUID>`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type the URL: `https://app.ally.io/`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [Ally.io Client support team](mailto:contact@ally.io) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. Ally.io application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot that shows the list of default attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

8. In addition to above, Ally.io application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | email | user.userprincipalname |
   | firstName | user.givenname |
   | lastName | user.surname |
9. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

10. In the **Set up Ally.io** section, copy the appropriate URL\(s\) based on your requirement.

    ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Ally.io SSO

To configure single sign-on on Ally.io side, you need to copy the Certificate \(Base64\) and appropriate URLs from Azure portal and add them in Ally.io.

1. Sign in to Ally.io using an Admin account.
2. Using the navigation bar on the left of the screen, select **Admin** > **Integrations**.
3. Scroll to the **Authentication** section and select **Single Sign-On**. Then, select **Enable**.

   ![Screenshot that shows the Enable button in Ally I O.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ally-tutorial/ally-enable.png)


   The **SSO Configuration** page opens, and you can configure the certificate and the copied URLs.


   ![Screenshot that shows the S S O configuration pane in Ally I O.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ally-tutorial/ally-single-sign-on-configuration.png)

4. In **SSO Configuration**, enter or select the following settings:

   - **Ally**: Microsoft Entra ID
   - **SAML 2.0 Endpoint URL**: Login URL
   - **Identity Provider Issuer URL**: Microsoft Entra Identifier
   - **Public\(X.509\) Certificate**: Certificate \(base 64\)

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Ally.io Sign on URL where you can initiate the login flow.
- Go to Ally.io Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Ally.io for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Ally.io tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Ally.io for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Ally.io you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
