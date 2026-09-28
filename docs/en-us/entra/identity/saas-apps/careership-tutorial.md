<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/careership-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure CAREERSHIP for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate CAREERSHIP with Microsoft Entra ID. CAREERSHIP is the NO.1 LMS \(LEARNING MANAGEMENT SYSTEM\) for Enterprises. It's an LMS that has continued to evolve while responding to the demands of Japan companies, and while it's high performance and multi-functional, it's also easy to use at the same time. When you integrate CAREERSHIP with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to CAREERSHIP.
- Enable your users to be automatically signed-in to CAREERSHIP with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You configure and test Microsoft Entra single sign-on for CAREERSHIP in a test environment. CAREERSHIP supports **SP** initiated single sign-on.

## Prerequisites

To integrate Microsoft Entra ID with CAREERSHIP, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- CAREERSHIP single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the CAREERSHIP application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add CAREERSHIP from the Microsoft Entra gallery

Add CAREERSHIP from the Microsoft Entra application gallery to configure single sign-on with CAREERSHIP. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **CAREERSHIP** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type a value using the following pattern: `https://<tenant_name>.learningpark.jp/e/`

   b. In the **Reply URL** textbox, type a URL using the following pattern: `https://<tenant_name>.learningpark.jp/e/SamlListener`

   c. In the **Sign on URL** textbox, type a URL using the following pattern: `https://<tenant_name>.learningpark.jp/e/Saml?corp_code=<corporate_code>`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [CAREERSHIP support team](mailto:asp-support@lightworks.co.jp) to get these values. You can also refer to the patterns shown in the Basic SAML Configuration section.
6. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

7. On the **Set up CAREERSHIP** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration appropriate URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

## Configure CAREERSHIP SSO

To configure single sign-on on **CAREERSHIP** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [CAREERSHIP support team](mailto:asp-support@lightworks.co.jp). They set this setting to have the SAML SSO connection set properly on both sides.

### Create CAREERSHIP test user

In this section, you create a user called Britta Simon at CAREERSHIP. Work with [CAREERSHIP support team](mailto:asp-support@lightworks.co.jp) to add the users in the CAREERSHIP platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to CAREERSHIP Sign-on URL where you can initiate the login flow.
- Go to CAREERSHIP Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the CAREERSHIP tile in the My Apps, this option redirects to CAREERSHIP Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure CAREERSHIP you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
