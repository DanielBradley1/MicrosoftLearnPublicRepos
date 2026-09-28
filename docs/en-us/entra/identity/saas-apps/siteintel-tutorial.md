<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/siteintel-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure SiteIntel for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate SiteIntel with Microsoft Entra ID. When you integrate SiteIntel with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to SiteIntel.
- Enable your users to be automatically signed in to SiteIntel with their Microsoft Entra accounts.
- Manage your accounts in one central location, the Azure portal.

To learn more about software as a service \(SaaS\) app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- SiteIntel single sign-on \(SSO\)-enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- SiteIntel supports SP-initiated and IdP-initiated SSO.
- After you configure SiteIntel, you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).

## Add SiteIntel from the gallery

To configure the integration of SiteIntel into Microsoft Entra ID, you need to add SiteIntel from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** box, enter **SiteIntel**.
4. In the results list, select **SiteIntel**, and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra single sign-on for SiteIntel

Configure and test Microsoft Entra SSO with SiteIntel by using a test user called *B.Simon*. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in SiteIntel.

To configure and test Microsoft Entra SSO with SiteIntel, complete the following building blocks:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** to enable your users to use this feature.

   a. **Create a Microsoft Entra test user** to test Microsoft Entra single sign-on with user B.Simon.

   b. **Assign the Microsoft Entra test user** to enable user B.Simon to use Microsoft Entra single sign-on.
2. **[Configure SiteIntel SSO](#configure-siteintel-sso)** to configure the single sign-on settings on the application side.

   - **[Create a SiteIntel test user](#create-a-siteintel-test-user)** to have a counterpart of user B.Simon in SiteIntel that's linked to the Microsoft Entra representation of the user.

3. **[Test SSO](#test-sso)** to verify that the configuration works.

## Configure Microsoft Entra SSO

To enable Microsoft Entra SSO in the Azure portal, do the following:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **SiteIntel** application integration page, go to the **Manage** section, and then select **single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, next to **Basic SAML Configuration**, select **Edit** \(pen icon\).

   ![Screenshot of "Set up Single-Sign-On with SAML" pane](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. To configure the application in IdP-initiated mode, in the **Basic SAML Configuration** section, do the following:

   a. In the **Identifier** box, type a URL in the following format: `urn:amazon:cognito:sp:<REGION>_<USERPOOLID>`

   b. In the **Reply URL** box, type a URL in the following format: `https://<CLIENT>.auth.siteintel.com/saml2/idpresponse`

   c. In the **Relay State** box, type a URL in the following format: `https://<CLIENT>.siteintel.com`
6. To configure the application in SP-initiated mode, select **Set additional URLs**, and then do the following:

   - In the **Sign-on URL** box, type a URL in the following format: `https://<CLIENT>.siteintel.com`


   Note


   These values aren't real. Update them with the actual Identifier, Reply URL, Sign-on URL, and Relay State. To get these values, contact [SiteIntel Client support team](mailto:support@intalytics.com). You can also refer to the patterns shown in the **Basic SAML Configuration** section.

7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select the **Copy** button to copy the URL in the **App Federation Metadata Url** box.

   ![Screenshot of the "App Federation Metadata URL" Copy button](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure SiteIntel SSO

To configure single sign-on on the SiteIntel side, send the URL you copied from the **App Federation Metadata Url** box to the [SiteIntel support team](mailto:support@intalytics.com). They set this value to establish the SAML SSO connection properly on both sides.

### Create a SiteIntel test user

In this section, you create a user called *Britta Simon* in SiteIntel. Work with [SiteIntel support team](mailto:support@intalytics.com) to add the users in the SiteIntel platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration by using the Access Panel.

When you select the **SiteIntel** tile in the Access Panel, you should be automatically signed in to the SiteIntel for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional resources

- [List of articles about how to integrate SaaS apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What are application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
- [What is session control in Microsoft Defender for Cloud Apps?](https://learn.microsoft.com/en-us/cloud-app-security/proxy-intro-aad)
- [How to protect SiteIntel with advanced visibility and controls](https://learn.microsoft.com/en-us/cloud-app-security/proxy-intro-aad)
