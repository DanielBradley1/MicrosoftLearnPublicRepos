<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/trelica-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Trelica for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Trelica with Microsoft Entra ID. When you integrate Trelica with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Trelica.
- Enable your users to be automatically signed in to Trelica with their Microsoft Entra accounts.
- Manage your accounts in one central location: the Azure portal.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A Trelica subscription with single sign-on \(SSO\) enabled.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Trelica supports IDP-initiated SSO.
- Trelica supports just-in-time user provisioning.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Trelica from the gallery

To configure the integration of Trelica into Microsoft Entra ID, you need to add Trelica from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, enter **Trelica** in the search box.
4. Select **Trelica** from the search results, and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Trelica

Configure and test Microsoft Entra SSO with Trelica by using a test user called **B.Simon**. For SSO to work, you must establish a linked relationship between a Microsoft Entra user and the related user in Trelica.

To configure and test Microsoft Entra SSO with Trelica, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Trelica SSO](#configure-trelica-sso)** to configure the single sign-on settings on the application side.

   1. **[Create a Trelica test user](#create-a-trelica-test-user)** to have a counterpart of B.Simon in Trelica. This counterpart is linked to the Microsoft Entra representation of the user.

3. **[Test SSO](#test-sso)** to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Azure portal:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Trelica** application integration page, go to the **Manage** section. Select **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up Single Sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![The Set up Single Sign-On with SAML page, with the pencil icon for Basic SAML Configuration highlighted](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   1. In the **Identifier** box, type the URL: `https://app.trelica.com`.
   2. In the **Reply URL** box, type a URL using the following pattern: `https://app.trelica.com/Id/Saml2/<CUSTOM_IDENTIFIER>/Acs`.


   Note


   The Reply URL value isn't real. Update this value with the actual Reply URL \(also known as the ACS\). You can find this by logging in to Trelica and going to the [SAML identity providers configuration page](https://app.trelica.com/Admin/Profile/SAML) \(Admin > Account > SAML\). Select the copy button next to the **Assertion Consumer Service \(ACS\) URL** to put this onto the clipboard, ready for pasting into the **Reply URL** text box in Microsoft Entra ID. Read the [Trelica help documentation](https://docs.trelica.com/admin/saml/azure-ad) or contact the [Trelica Client support team](mailto:support@trelica.com) if you have questions.

6. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select the copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The SAML Signing Certificate section, with the copy button highlighted next to App Federation Metadata URL](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Trelica SSO

To configure single sign-on on the **Trelica** side, go to the [SAML identity providers configuration page](https://app.trelica.com/Admin/Profile/SAML) \(Admin > Account > SAML\). Select the **New** button. Enter **Microsoft Entra ID** as the Name and choose **Metadata from url** for the Metadata type. Paste the **App Federation Metadata Url** you took from Microsoft Entra ID into the **Metadata url** field in Trelica.

Read the [Trelica help documentation](https://docs.trelica.com/admin/saml/azure-ad) or contact the [Trelica Client support team](mailto:support@trelica.com) if you have questions.

### Create a Trelica test user

Trelica supports just-in-time user provisioning, which is enabled by default. There's no action for you to take in this section. If a user doesn't already exist in Trelica, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the Trelica for which you set up the SSO.
- You can use Microsoft My Apps. When you select the Trelica tile in the My Apps, you should be automatically signed in to the Trelica for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Trelica you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
