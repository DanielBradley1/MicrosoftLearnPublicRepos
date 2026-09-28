<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/informatica-intelligent-data-management-cloud-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Informatica Intelligent Data Management Cloud for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Informatica Intelligent Data Management Cloud with Microsoft Entra ID. It's a SAML SSO Auth application to enable Informatica Intelligent Data Management Cloud on Azure Native Services. When you integrate Informatica Intelligent Data Management Cloud with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Informatica Intelligent Data Management Cloud.
- Enable your users to be automatically signed-in to Informatica Intelligent Data Management Cloud with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for Informatica Intelligent Data Management Cloud in a test environment. Informatica Intelligent Data Management Cloud supports both **SP** and **IDP** initiated single sign-on and **Just In Time** user provisioning.

## Prerequisites

To integrate Microsoft Entra ID with Informatica Intelligent Data Management Cloud, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Informatica Intelligent Data Management Cloud single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the Informatica Intelligent Data Management Cloud application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add Informatica Intelligent Data Management Cloud from the Microsoft Entra gallery

Add Informatica Intelligent Data Management Cloud from the Microsoft Entra application gallery to configure single sign-on with Informatica Intelligent Data Management Cloud. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Informatica Intelligent Data Management Cloud** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   1. In the **Identifier** textbox, type a URL using the following pattern: `https://<ORG_ID>.<REGION>.informaticacloud.com`
   2. In the **Reply URL** textbox, type a URL using the following pattern: `https://<REGION>.informaticacloud.com/identity-service/acs/<ORG_ID>`

6. If you wish to configure the application in **SP** initiated mode, then perform the following step:

   In the **Sign on URL** textbox, type a URL using the following pattern: `https://<REGION>.informaticacloud.com/ma/sso/<ORG_ID>`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [Informatica Intelligent Data Management Cloud support team](mailto:support@informatica.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png "Certificate")

8. On the **Set up Informatica Intelligent Data Management Cloud** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration appropriate URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

## Configure Informatica Intelligent Data Management Cloud SSO

1. Log in to your Informatica Intelligent Data Management Cloud company site as an administrator.
2. Go to **Administrator** > **SAML Setup** and perform the following steps:

   ![Screenshot that shows the Settings page of Brainfuse.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/informatica-intelligent-data-management-cloud-tutorial/settings.png "Business")


   1. In the **Issuer** textbox, paste the **Microsoft Entra Identifier** value, which you copied previously.
   2. In the **Single Sign-On Service URL** textbox, paste the **Login URL**, which you copied previously.
   3. In the **Single Logout Service URL** textbox, paste the **Logout URL**, which you copied previously.
   4. Open the downloaded **Certificate \(Base64\)** into Notepad and paste the content into the **Signing Certificate** textbox.
   5. Select **Save** to save the details.

### Create Informatica Intelligent Data Management Cloud test user

In this section, a user called B.Simon is created in Informatica Intelligent Data Management Cloud. Informatica Intelligent Data Management Cloud supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Informatica Intelligent Data Management Cloud, a new one is commonly created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Informatica Intelligent Data Management Cloud Sign-on URL where you can initiate the login flow.
- Go to Informatica Intelligent Data Management Cloud Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Informatica Intelligent Data Management Cloud for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Informatica Intelligent Data Management Cloud tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Informatica Intelligent Data Management Cloud for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure Informatica Intelligent Data Management Cloud you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
