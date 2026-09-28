<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/sciquest-spend-director-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure SciQuest Spend Director for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate SciQuest Spend Director with Microsoft Entra ID. When you integrate SciQuest Spend Director with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to SciQuest Spend Director.
- Enable your users to be automatically signed-in to SciQuest Spend Director with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- SciQuest Spend Director single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- SciQuest Spend Director supports **SP** initiated SSO.
- SciQuest Spend Director supports **Just In Time** user provisioning.

## Add SciQuest Spend Director from the gallery

To configure the integration of SciQuest Spend Director into Microsoft Entra ID, you need to add SciQuest Spend Director from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **SciQuest Spend Director** in the search box.
4. Select **SciQuest Spend Director** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for SciQuest Spend Director

Configure and test Microsoft Entra SSO with SciQuest Spend Director using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in SciQuest Spend Director.

To configure and test Microsoft Entra SSO with SciQuest Spend Director, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure SciQuest Spend Director SSO](#configure-sciquest-spend-director-sso)** - to configure the single sign-on settings on application side.

   1. **[Create SciQuest Spend Director test user](#create-sciquest-spend-director-test-user)** - to have a counterpart of B.Simon in SciQuest Spend Director that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **SciQuest Spend Director** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** box, type a URL using the following pattern: `https://<companyname>.sciquest.com`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<companyname>.sciquest.com/apps/Router/ExternalAuth/Login/<instancename>`

   c. In the **Sign-on URL** text box, type a URL using the following pattern: `https://<companyname>.sciquest.com/apps/Router/SAMLAuth/<instancename>`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [SciQuest Spend Director Client support team](https://www.jaggaer.com/contact-us/) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up SciQuest Spend Director** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure SciQuest Spend Director SSO

To configure single sign-on on **SciQuest Spend Director** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [SciQuest Spend Director support team](https://www.jaggaer.com/contact-us/). They set this setting to have the SAML SSO connection set properly on both sides.

### Create SciQuest Spend Director test user

The objective of this section is to create a user called Britta Simon in SciQuest Spend Director.

You need to contact your [SciQuest Spend Director support team](https://www.jaggaer.com/contact-us/) and provide them with the details about your test account to get it created.

Alternatively, you can also leverage just-in-time provisioning, a single sign-on feature that's supported by SciQuest Spend Director.  
If just-in-time provisioning is enabled, users are automatically created by SciQuest Spend Director during a single sign-on attempt if they don't exist. This feature eliminates the need to manually create single sign-on counterpart users.

To get just-in-time provisioning enabled, you need to contact your [SciQuest Spend Director support team](https://www.jaggaer.com/contact-us/).

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to SciQuest Spend Director Sign-on URL where you can initiate the login flow.
- Go to SciQuest Spend Director Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the SciQuest Spend Director tile in the My Apps, this option redirects to SciQuest Spend Director Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure SciQuest Spend Director you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
