<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/convercent-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Convercent \| Microsoft Docs for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Convercent with Microsoft Entra ID. When you integrate Convercent with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Convercent.
- Enable your users to be automatically signed-in to Convercent with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Convercent single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Convercent supports **SP** and **IDP** initiated SSO.

## Add Convercent from the gallery

To configure the integration of Convercent into Microsoft Entra ID, you need to add Convercent from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Convercent** in the search box.
4. Select **Convercent** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Convercent

Configure and test Microsoft Entra SSO with Convercent using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Convercent.

To configure and test Microsoft Entra SSO with Convercent, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Convercent SSO](#configure-convercent-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Convercent test user](#create-convercent-test-user)** - to have a counterpart of B.Simon in Convercent that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Convercent** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, If you wish to configure the application in **IDP** initiated mode, perform the following step:

   In the **Identifier** text box, type a URL using the following pattern: `https://<INSTANCE_NAME>.convercent.com/`
6. Select **Set additional URLs** and perform the following steps if you wish to configure the application in **SP** initiated mode:

   a. In the **Sign-on URL** text box, type a URL using the following pattern: `https://<INSTANCE_NAME>.convercent.com/`

   b. In the **Relay State** text box, type a URL using the following pattern: `https://<INSTANCE_NAME>.convercent.com/`

   Note

   These values aren't real. Update these values with the actual Identifier, Sign-On URL and Relay State. Contact [Convercent Client support team](https://www.convercent.com/customers/services/customer-support) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

8. On the **Set up Convercent** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Convercent SSO

To configure single sign-on on **Convercent** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Convercent support team](https://www.convercent.com/customers/services/customer-support). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Convercent test user

In this section, you create a user called Britta Simon in Convercent. Work with [Convercent support team](https://www.convercent.com/customers/services/customer-support) to add the users in the Convercent platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Convercent Sign on URL where you can initiate the login flow.
- Go to Convercent Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Convercent for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Convercent tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Convercent for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Convercent you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
