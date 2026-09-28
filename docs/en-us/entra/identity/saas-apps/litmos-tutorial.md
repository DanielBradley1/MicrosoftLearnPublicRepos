<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/litmos-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure SAP Litmos for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate SAP Litmos with Microsoft Entra ID. When you integrate SAP Litmos with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to SAP Litmos.
- Enable your users to be automatically signed-in to SAP Litmos with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- SAP Litmos single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- SAP Litmos supports **SP** and **IDP** initiated SSO.
- SAP Litmos supports **Just In Time** user provisioning.
- SAP Litmos supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/litmos-provisioning-tutorial).

## Add SAP Litmos from the gallery

To configure the integration of SAP Litmos into Microsoft Entra ID, you need to add SAP Litmos from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **SAP Litmos** in the search box.
4. Select **SAP Litmos** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for SAP Litmos

Configure and test Microsoft Entra SSO with SAP Litmos using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in SAP Litmos.

To configure and test Microsoft Entra SSO with SAP Litmos, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure SAP Litmos SSO](#configure-sap-litmos-sso)** - to configure the single sign-on settings on application side.

   1. **[Create SAP Litmos test user](#create-sap-litmos-test-user)** - to have a counterpart of B.Simon in SAP Litmos that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **SAP Litmos** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type one of the following URLs:

   | **Identifier** |
   | --- |
   | `https://<CustomerName>.litmos.com` |
   | `https://<CustomerName>.litmos.com.au` |
   | `https://<CustomerName>.litmoseu.com` |


   b. In the **Reply URL** text box, type one of the following URLs:


   | **Reply URL** |
   | --- |
   | `https://<CompanyName>.litmos.com/integration/splogin` |
   | `https://<CompanyName>.litmos.com/integration/splogin?IdP=1` |
   | `https://<CompanyName>.litmos.com/integration/splogin?IdP=2` |
   | `https://<CompanyName>.litmos.com/integration/splogin?IdP=3` |
   | `https://<CompanyName>.litmos.com/integration/splogin?IdP=14` |
   | `https://<CompanyName>.litmos.com.au/integration/splogin` |
   | `https://<CompanyName>.litmos.com.au/integration/splogin?IdP=1` |
   | `https://<CompanyName>.litmos.com.au/integration/splogin?IdP=2` |
   | `https://<CompanyName>.litmos.com.au/integration/splogin?IdP=3` |
   | `https://<CompanyName>.litmos.com.au/integration/splogin?IdP=14` |
   | `https://<CompanyName>.litmoseu.com/integration/splogin` |
   | `https://<CompanyName>.litmoseu.com/integration/splogin?IdP=1` |
   | `https://<CompanyName>.litmoseu.com/integration/splogin?IdP=2` |
   | `https://<CompanyName>.litmoseu.com/integration/splogin?IdP=3` |
   | `https://<CompanyName>.litmoseu.com/integration/splogin?IdP=14` |


   c. In the **Sign on URL** text box, type one of the following URLs:


   | **Sign on URL** |
   | --- |
   | `https://<CompanyName>.litmos.com/integration/splogin` |
   | `https://<CompanyName>.litmos.com/integration/splogin?IdP=1` |
   | `https://<CompanyName>.litmos.com/integration/splogin?IdP=2` |
   | `https://<CompanyName>.litmos.com/integration/splogin?IdP=3` |
   | `https://<CompanyName>.litmos.com/integration/splogin?IdP=14` |
   | `https://<CompanyName>.litmos.com.au/integration/splogin` |
   | `https://<CompanyName>.litmos.com.au/integration/splogin?IdP=1` |
   | `https://<CompanyName>.litmos.com.au/integration/splogin?IdP=2` |
   | `https://<CompanyName>.litmos.com.au/integration/splogin?IdP=3` |
   | `https://<CompanyName>.litmos.com.au/integration/splogin?IdP=14` |
   | `https://<CompanyName>.litmoseu.com/integration/splogin` |
   | `https://<CompanyName>.litmoseu.com/integration/splogin?IdP=1` |
   | `https://<CompanyName>.litmoseu.com/integration/splogin?IdP=2` |
   | `https://<CompanyName>.litmoseu.com/integration/splogin?IdP=3` |
   | `https://<CompanyName>.litmoseu.com/integration/splogin?IdP=14` |


   d. In the **Relay State URL** text box, type one of the following URLs:


   | **Relay State URL** |
   | --- |
   | `https://<CompanyName>.litmos.com/integration/splogin?RelayState=https://<CustomerName>.litmos.com/Course/12345` |
   | `https://<CompanyName>.litmos.com/integration/splogin?RelayState=https://<CustomerName>.litmos.com/LearningPath/12345` |


   Note


   These values aren't real. Update these values with the actual Identifier, Reply URL, Sign on URL and Relay State URL which are explained later in article or contact [SAP Litmos Client support team](https://www.litmos.com/contact-us) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up SAP Litmos** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure SAP Litmos SSO

1. In a different browser window, sign-on to your SAP Litmos company site as administrator.
2. In the navigation bar on the left side, select **Accounts**.

   ![Accounts Section on App Side](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/litmos-tutorial/account.png)

3. Select the **Integrations** tab.

   ![Integration Tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/litmos-tutorial/integrate.png)

4. On the **Integrations** tab, scroll down to **3rd Party Integrations**, and then select **SAML 2.0** tab.

   ![SAML 2.0 Section](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/litmos-tutorial/third-party.png)

5. Copy the value under **The SAML endpoint for litmos is:** and paste it into the **Reply URL** textbox in the **Litmos Domain and URLs** section in Azure portal.

   ![SAML endpoint](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/litmos-tutorial/certificate.png)

6. In your **SAP Litmos** application, perform the following steps:

   ![Litmos Application](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/litmos-tutorial/application.png)


   a. Select **Enable SAML**.


   b. Open your base-64 encoded certificate in notepad, copy the content of it into your clipboard, and then paste it to the **SAML X.509 Certificate** textbox.


   c. Select **Save Changes**.

### Create SAP Litmos test user

In this section, a user called B.Simon is created in SAP Litmos. SAP Litmos supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in SAP Litmos, a new one is created after authentication.

**To create a user called Britta Simon in SAP Litmos, perform the following steps:**

1. In a different browser window, sign-on to your SAP Litmos company site as administrator.
2. In the navigation bar on the left side, select **Accounts**.

   ![Accounts Section On App Side](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/litmos-tutorial/account.png)

3. Select the **Integrations** tab.

   ![Integrations Tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/litmos-tutorial/integrate.png)

4. On the **Integrations** tab, scroll down to **3rd Party Integrations**, and then select **SAML 2.0** tab.

   ![SAML 2.0](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/litmos-tutorial/third-party.png)

5. Select **Autogenerate Users**

   ![Autogenerate Users](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/litmos-tutorial/users.png)

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to SAP Litmos Sign on URL where you can initiate the login flow.
- Go to SAP Litmos Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the SAP Litmos for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the SAP Litmos tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the SAP Litmos for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure SAP Litmos you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
