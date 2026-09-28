<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/eccentex-appbase-for-azure-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Eccentex AppBase for Azure for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Eccentex AppBase for Azure with Microsoft Entra ID. When you integrate Eccentex AppBase for Azure with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Eccentex AppBase for Azure.
- Enable your users to be automatically signed-in to Eccentex AppBase for Azure with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Eccentex AppBase for Azure single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Eccentex AppBase for Azure supports **SP** initiated SSO.
- Eccentex AppBase for Azure supports **Just In Time** user provisioning.

## Add Eccentex AppBase for Azure from the gallery

To configure the integration of Eccentex AppBase for Azure into Microsoft Entra ID, you need to add Eccentex AppBase for Azure from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Eccentex AppBase for Azure** in the search box.
4. Select **Eccentex AppBase for Azure** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Eccentex AppBase for Azure

Configure and test Microsoft Entra SSO with Eccentex AppBase for Azure using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Eccentex AppBase for Azure.

To configure and test Microsoft Entra SSO with Eccentex AppBase for Azure, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Eccentex AppBase for Azure SSO](#configure-eccentex-appbase-for-azure-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Eccentex AppBase for Azure test user](#create-eccentex-appbase-for-azure-test-user)** - to have a counterpart of B.Simon in Eccentex AppBase for Azure that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Eccentex AppBase for Azure** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using one of the following patterns:

   | **Identifier** |
   | --- |
   | `https://<CustomerName>.appbase.com/Ecx.Web` |
   | `https://<CustomerName>.eccentex.com:<PortNumber>/Ecx.Web` |


   b. In the **Sign on URL** text box, type a URL using one of the following patterns:


   | **Sign on URL** |
   | --- |
   | `https://<CustomerName>.appbase.com/Ecx.Web/Account/sso?tenantCode=<TenantCode>&authCode=<AuthConfigurationCode>` |
   | `https://<CustomerName>.eccentex.com:<PortNumber>/Ecx.Web/Account/sso?tenantCode=<TenantCode>&authCode=<AuthConfigurationCode>` |


   Note


   These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [Eccentex AppBase for Azure Client support team](mailto:eccentex.support@eccentex.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Raw\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificateraw.png)

7. On the **Set up Eccentex AppBase for Azure** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Eccentex AppBase for Azure SSO

1. Log in to your Eccentex AppBase for Azure company site as an administrator.
2. Go to **Gear** icon and select **Manage Users**.

   ![Screenshot shows settings of SAML account.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/eccentex-appbase-for-azure-tutorial/settings.png "Account")

3. Navigate to **User Management** > **Auth Configurations** and select **Add SAML** button.
4. In the **New SAML Configuration** page, perform the following steps.

   ![Screenshot shows the Azure SAML configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/eccentex-appbase-for-azure-tutorial/configuration.png "SAML Configuration")


   1. In the **Name** textbox, type a short configuration name.
   2. In the **Issuer Url** textbox, enter the Azure **Application ID** which you copied previously.
   3. Copy **Application Url** value, paste this value into the **Identifier\(Entity ID\)** text box in the **Basic SAML Configuration** section.
   4. In the **AppBase New Users Onboarding**, select **Invitation Only** from the dropdown.
   5. In the **AppBase Authentication Failure Behavior**, select **Display Error Page** from the dropdown.
   6. Select **Signature Digest Method** and **Signature Method** according to your certificate encryption.
   7. In the **Use Certificate**, select **Manual Uploading** from the dropdown.
   8. In the **Authentication Context Class Name**, select **Password** from the dropdown.
   9. In the **Service Provider to Identity Provider Binding**, select **HTTP-Redirect** from the dropdown.

      Note

      Make sure the **Sign Outbound Requests** isn't checked.
   10. Copy **Assertion Consumer Service Url** value, paste this value into the **Reply URL** text box in the **Basic SAML Configuration** section.
   11. In the **Auth Request Destination Url** textbox, paste the **Login URL** value which you copied previously.
   12. In the **Service Provider Resource URL** textbox, paste the **Login URL** value which you copied previously.
   13. In the **Artifact Identification Url** textbox, paste the **Login URL** value which you copied previously.
   14. In the **Auth Request Protocol Binding**, select **HTTP-POST** from the dropdown.
   15. In the **Auth Request Name ID Policy**, select **Persistent** from the dropdown.
   16. In the **Artifact Responder URL** textbox, paste the **Login URL** value which you copied previously.
   17. Enable **Enforce Response Signature Verification** checkbox.
   18. Open the downloaded **Certificate\(Raw\)** into Notepad and paste the content into the **SAML Mutual Certificate Upload** textbox.
   19. In the **Logout Response Protocol Binding**, select **HTTP-POST** from the dropdown.
   20. In the **AppBase Custom Logout URL** textbox, paste the **Logout URL** value which you copied previously.
   21. Select **Save**.

### Create Eccentex AppBase for Azure test user

In this section, a user called Britta Simon is created in Eccentex AppBase for Azure. Eccentex AppBase for Azure supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Eccentex AppBase for Azure, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Eccentex AppBase for Azure Sign-on URL where you can initiate the login flow.
- Go to Eccentex AppBase for Azure Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Eccentex AppBase for Azure tile in the My Apps, this option redirects to Eccentex AppBase for Azure Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Eccentex AppBase for Azure you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
