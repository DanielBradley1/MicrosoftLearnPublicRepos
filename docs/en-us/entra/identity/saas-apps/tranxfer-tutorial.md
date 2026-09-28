<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/tranxfer-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Tranxfer' for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Tranxfer with Microsoft Entra ID. Tranxfer provides the safest and easiest to use business solution for sending and receiving files. When you integrate Tranxfer with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Tranxfer.
- Enable your users to be automatically signed-in to Tranxfer with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for Tranxfer in a test environment. Tranxfer supports **SP** initiated single sign-on and **Just In Time** user provisioning.

## Prerequisites

To integrate Microsoft Entra ID with Tranxfer, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Tranxfer single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the Tranxfer application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add Tranxfer from the Microsoft Entra gallery

Add Tranxfer from the Microsoft Entra application gallery to configure single sign-on with Tranxfer. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Tranxfer** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:-

   a. In the **Identifier** textbox, type a URL using the following pattern: `https://<SUBDOMAIN>.tranxfer.com`

   b. In the **Reply URL** textbox, type a URL using the following pattern: `https://<SUBDOMAIN>.tranxfer.com/SAMLResponse`

   c. In the **Sign on URL** textbox, type a URL using the following pattern: `https://<SUBDOMAIN>.tranxfer.com/saml/login`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [Tranxfer Client support team](mailto:soporte@tranxfer.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. Tranxfer application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Attributes")

7. In addition to above, Tranxfer application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | groups | user.groups \[All\] |
8. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

## Configure Tranxfer SSO

You'll need to log in to your Tranxfer application with the company administrator account.

1. Go to **Settings -> SAML** and paste **App Federation Metadata Url** to **Metadata URL** field.
2. If you want to give specific permissions to different user groups, you can match Microsoft Entra groups to common **Tranxfer** permissions. To do so, fill in Microsoft Entra group ID for each permission:

   a. SEND permission to send files.

   b. RECEIVE to receive files.

   c. SEND + RECEIVE both of the above.

   d. ADMIN company administration permission but not sending nor receiving files.

   e. FULL all of the above.

   ![Screenshot shows Tranxfer SAML settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/tranxfer-tutorial/tranxfer-saml-settings.png "Tranxfer SAML Settings")

3. If you want to give any user of your organization, the simple Send and Receive permission no matter which groups they have, enable the **Empty groups with permission** option.
4. If you want only match permissions by groups but don't want to import Microsoft Entra groups to Tranxfer groups enable the **Disable import groups** option.

If you find any problems, please contact [Tranxfer support team](mailto:soporte@tranxfer.com). The support team will assist you in configuring the single sign-on on the application.

### Create Tranxfer test user

In this section, a user called B.Simon is created in Tranxfer. Tranxfer supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Tranxfer, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Tranxfer Sign-on URL where you can initiate the login flow.
- Go to Tranxfer Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Tranxfer tile in the My Apps, this option redirects to Tranxfer Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure Tranxfer you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
