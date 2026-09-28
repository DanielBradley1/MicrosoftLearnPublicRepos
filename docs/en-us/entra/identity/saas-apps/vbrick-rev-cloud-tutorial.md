<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/vbrick-rev-cloud-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Vbrick Rev Cloud for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Vbrick Rev Cloud with Microsoft Entra ID. Rev enterprise video platform is a solution to capture, manage and distribute live and on-demand video. We help organizations meet critical live video needs and innovative uses of on-demand videos. When you integrate Vbrick Rev Cloud with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Vbrick Rev Cloud.
- Enable your users to be automatically signed-in to Vbrick Rev Cloud with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for Vbrick Rev Cloud in a test environment. Vbrick Rev Cloud supports **SP** initiated single sign-on and [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/vbrick-rev-cloud-provisioning-tutorial).

## Prerequisites

To integrate Microsoft Entra ID with Vbrick Rev Cloud, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Vbrick Rev Cloud single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the Vbrick Rev Cloud application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add Vbrick Rev Cloud from the Microsoft Entra gallery

Add Vbrick Rev Cloud from the Microsoft Entra application gallery to configure single sign-on with Vbrick Rev Cloud. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Vbrick Rev Cloud** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   [![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png#lightbox)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type a URL using one of the following patterns:

   | **Identifier** |
   | --- |
   | `https://<CustomerName>.domain.extension:443` |
   | `https://<CustomerName>.au.vbrickrev.com:443` |
   | `https://<CustomerName>.eu.vbrickrev.com:443` |
   | `https://<CustomerName>.rev.vbrick.com:443` |


   b. In the **Reply URL** textbox, type a URL using one of the following patterns:


   | **Reply URL** |
   | --- |
   | `https://<CustomerName>.rev.vbrick.com:443/sso/consume` |
   | `https://<CustomerName>.eu.vbrickrev.com:443/sso/consume` |
   | `https://<CustomerName>.au.vbrickrev.com:443/sso/consume` |
   | `https://<CustomerName>.domain.extension:443/sso/consume` |


   c. In the **Sign on URL** textbox, type a URL using one of the following patterns:


   | **Sign on URL** |
   | --- |
   | `https://<CustomerName>.rev.vbrick.com` |
   | `https://<CustomerName>.eu.vbrickrev.com` |
   | `https://<CustomerName>.au.vbrickrev.com` |
   | `https://<CustomerName>.domain.extension` |


   Note


   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [Vbrick Rev Cloud support team](mailto:support@vbrick.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   [![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png#lightbox)

7. On the **Set up Vbrick Rev Cloud** section, copy the appropriate URL\(s\) based on your requirement.

   [![Screenshot shows to copy configuration appropriate URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png#lightbox)

## Configure Vbrick Rev Cloud

1. Log in to your Vbrick Rev Cloud company site as an administrator.
2. Navigate to **System Settings** > **Security**.
3. In the **SAML SINGLE SIGN ON** section, perform the following steps:

   [![Screenshot shows the administration portal.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/vbrick-rev-cloud-tutorial/manage.png "Admin")](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/vbrick-rev-cloud-tutorial/manage.png#lightbox)


   1. Check the **Enable Single Sign On** checkbox.
   2. In **Identity Provider Metadata** textbox, paste the **Federation Metadata XML** file, which you copied previously.
   3. For **Signature Algorithm**, select **SHA256WithRSA** from the dropdown list.
   4. Leave the **Sign SAML Request** checkbox checked and select **Save**.


   Note


   For more information, please visit [this](https://revdocs.vbrick.com/docs/configure-single-sign-on-sso) Vbrick Rev documentation.

### Create Vbrick Rev Cloud test user

In this section, you create a user called B.Simon in Vbrick Rev. Please follow [this](https://revdocs.vbrick.com/docs/user-accounts#add-or-edit-a-user) guide to create the test user. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Vbrick Rev Cloud Sign-on URL where you can initiate the login flow.
- Go to Vbrick Rev Cloud Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Vbrick Rev Cloud tile in the My Apps, this option redirects to Vbrick Rev Cloud Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure Vbrick Rev Cloud you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
