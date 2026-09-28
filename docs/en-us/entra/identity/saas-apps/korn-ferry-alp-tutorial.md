<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/korn-ferry-alp-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Korn Ferry ALP for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Korn Ferry ALP with Microsoft Entra ID. When you integrate Korn Ferry ALP with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Korn Ferry ALP.
- Enable your users to be automatically signed-in to Korn Ferry ALP with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Korn Ferry ALP single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Korn Ferry ALP supports **SP** initiated SSO.

## Add Korn Ferry ALP from the gallery

To configure the integration of Korn Ferry ALP into Microsoft Entra ID, you need to add Korn Ferry ALP from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Korn Ferry ALP** in the search box.
4. Select **Korn Ferry ALP** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Korn Ferry ALP

Configure and test Microsoft Entra SSO with Korn Ferry ALP using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Korn Ferry ALP.

To configure and test Microsoft Entra SSO with Korn Ferry ALP, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Korn Ferry ALP SSO](#configure-korn-ferry-alp-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Korn Ferry ALP test user](#create-korn-ferry-alp-test-user)** - to have a counterpart of B.Simon in Korn Ferry ALP that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Korn Ferry ALP** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using one of the following patterns:

   | **Identifier** |
   | --- |
   | `https://intappextin01/portalweb/sso/client/audience?guid=<customerguid>` |
   | `https://qaassessment.kfnaqa.com/portalweb/sso/client/audience?guid=<customerguid>` |
   | `https://assessments.kornferry.com/portalweb/sso/client/audience?guid=<customerguid>` |


   b. In the **Sign on URL** text box, type a URL using one of the following patterns:


   | **Sign on URL** |
   | --- |
   | `https://intappextin01/portalweb/sso/client/audience?guid=<customerguid>` |
   | `https://qaassessment.kfnaqa.com/portalweb/sso/client/audience?guid=<customerguid>` |
   | `https://assessments.kornferry.com/portalweb/sso/client/audience?guid=<customerguid>` |


   Note


   These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [Korn Ferry ALP Client support team](mailto:noreply@kornferry.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up Single Sign-On with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Korn Ferry ALP SSO

To configure single sign-on on **Korn Ferry ALP** side, you need to send the **App Federation Metadata Url** to [Korn Ferry ALP support team](mailto:noreply@kornferry.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Korn Ferry ALP test user

In this section, you create a user called Britta Simon in Korn Ferry ALP. Work with [Korn Ferry ALP support team](mailto:noreply@kornferry.com) to add the users in the Korn Ferry ALP platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Korn Ferry ALP Sign-on URL where you can initiate the login flow.
- Go to Korn Ferry ALP Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Korn Ferry ALP tile in the My Apps, this option redirects to Korn Ferry ALP Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Korn Ferry ALP you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
