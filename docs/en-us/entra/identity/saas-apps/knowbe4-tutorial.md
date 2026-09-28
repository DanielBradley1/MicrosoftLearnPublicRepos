<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/knowbe4-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure KnowBe4 Security Awareness Training for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate KnowBe4 Security Awareness Training with Microsoft Entra ID. When you integrate KnowBe4 Security Awareness Training with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to KnowBe4 Security Awareness Training.
- Enable your users to be automatically signed-in to KnowBe4 Security Awareness Training with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- KnowBe4 Security Awareness Training single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- KnowBe4 Security Awareness Training supports **SP** initiated SSO.
- KnowBe4 Security Awareness Training supports **Just In Time** user provisioning.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add KnowBe4 from the gallery

To configure the integration of KnowBe4 into Microsoft Entra ID, you need to add KnowBe4 from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **KnowBe4** in the search box.
4. Select **KnowBe4** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for KnowBe4 Security Awareness Training

In this section, you configure and test Microsoft Entra single sign-on with KnowBe4 based on a test user called **Britta Simon**. For single sign-on to work, a link relationship between a Microsoft Entra user and the related user in KnowBe4 needs to be established.

To configure and test Microsoft Entra single sign-on with KnowBe4, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra SSO with Britta Simon.
   2. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra SSO.

2. **[Configure KnowBe4 Security Awareness Training SSO](#configure-knowbe4-security-awareness-training-sso)** - to configure the SSO settings on application side.

   1. **[Create KnowBe4 Security Awareness Training test user](#create-knowbe4-security-awareness-training-test-user)** - to have a counterpart of Britta Simon in KnowBe4 Security Awareness Training that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **KnowBe4** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following step:

   In the **Sign on URL** text box, type a URL using the following pattern: `https://<companyname>.KnowBe4.com/auth/saml/<instancename>`

   Note

   The sign on URL value isn't real. Update this value with the actual Sign on URL. Contact [KnowBe4 Security Awareness Training Client support team](mailto:support@KnowBe4.com) to get this value. You can also refer to the pattern shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Raw\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificateraw.png)

7. On the **Set up KnowBe4 Security Awareness Training** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure KnowBe4 Security Awareness Training SSO

To configure single sign-on on **KnowBe4 Security Awareness Training** side, you need to send the downloaded **Certificate \(Raw\)** and appropriate copied URLs from the application configuration to [KnowBe4 Security Awareness Training support team](mailto:support@KnowBe4.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create KnowBe4 Security Awareness Training test user

In this section, a user called Britta Simon is created in KnowBe4. KnowBe4 supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in KnowBe4, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to KnowBe4 Security Awareness Training Sign-on URL where you can initiate the login flow.
- Go to KnowBe4 Security Awareness Training Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the KnowBe4 Security Awareness Training tile in the My Apps, this option redirects to KnowBe4 Security Awareness Training Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure KnowBe4 Security Awareness Training you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
