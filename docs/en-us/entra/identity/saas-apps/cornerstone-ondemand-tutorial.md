<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/cornerstone-ondemand-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Configure Cornerstone for Single sign-on with Microsoft Entra ID

In this article, you learn how to set up the single sign-on integration between Cornerstone and Microsoft Entra ID. When you integrate Cornerstone with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has SSO access to Cornerstone.
- Enable your users to be automatically signed-in to Cornerstone with their Microsoft Entra accounts.
- Manage your accounts in one central location.

Cornerstone is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Enabled SSO in Cornerstone.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Cornerstone supports **SP** initiated SSO.
- Cornerstone supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/cornerstone-ondemand-provisioning-tutorial).
- If you're integrating one or multiple products from this particular list then you should use this Cornerstone Single Sign-On app from the Gallery.

  We offer solutions for :

  1. Recruiting
  2. Learning
  3. Development
  4. Content
  5. Performance
  6. Career
  7. HR

## Adding Cornerstone Single Sign-On from the gallery

To configure the Microsoft Entra SSO integration with Cornerstone, you need to...

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Cornerstone Single Sign-On** in the search box.
4. Select **Cornerstone Single Sign-On** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Cornerstone

Configure and test Microsoft Entra SSO with Cornerstone using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Cornerstone.

To configure and test Microsoft Entra SSO with Cornerstone, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Cornerstone Single Sign-On](#configure-cornerstone-single-sign-on)** - to configure the SSO in Cornerstone.

   1. **[Create Cornerstone Single Sign-On test user](#create-cornerstone-single-sign-on-test-user)** - to have a counterpart of B.Simon in Cornerstone that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.
4. **[Test SSO for Cornerstone \(Mobile\)](#test-sso-for-cornerstone-mobile)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Cornerstone Single Sign-On** application integration page, find the **Manage** section and select **Single sign-on**.
3. On the **Select a Single sign-on method** page, select **SAML**.
4. On the **Set up Single Sign-On with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://<PORTAL_NAME>.csod.com`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<PORTAL_NAME>.csod.com/samldefault.aspx?ouid=<OUID>`

   c. In the **Sign on URL** text box, type a URL using the following pattern: `https://<PORTAL_NAME>.csod.com/samldefault.aspx?ouid=<OUID>`

   Note

   These values aren't real. Update these values with the actual Reply URL, Identifier and Sign on URL. Please reach out to your Cornerstone implementation project team to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up Cornerstone Single Sign-On** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Cornerstone Single Sign-On

To configure SSO in Cornerstone, you need to reach out to your Cornerstone implementation project team. They set this setting to have the SAML SSO connection set properly on both sides.

### Create Cornerstone Single Sign-On test user

In this section, you create a user called Britta Simon in Cornerstone. Please work with your Cornerstone implementation project team to add the users in Cornerstone. Users must be created and activated before you use single sign-on.

Cornerstone Single Sign-On also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/cornerstone-ondemand-provisioning-tutorial) on how to configure automatic user provisioning.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Cornerstone Sign-on URL where you can initiate the login flow.
- Go to Cornerstone Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Cornerstone Single Sign-On tile in the My Apps, this option redirects to Cornerstone Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Test SSO for Cornerstone \(Mobile\)

1. In a different browser window, log in to your Cornerstone website as an administrator and perform the following steps.

   a. Go to the **Admin -> Tools -> CORE FUNCTIONS -> Core Preferences -> Authentication Preferences**.

   ![Screenshot for Authentication Preferences mobile application Cornerstone.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cornerstone-ondemand-tutorial/division-mobile.png)


   b. Search the **Division Name** by giving the Division Name in the search box.


   c. Select the **Division Name** in the results.


   d. From the SAML/IDP server URL dropdown, select the appropriate SAML/IDP server that should be used for user Authentication.


   ![Screenshot for Other credentials validated against client SAML/IDP server.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cornerstone-ondemand-tutorial/other-credentials.png)


   e. Select **Save**.

2. Go to **Admin > Tools > Core Functions > Core Preferences > Mobile**.

   a. Select the appropriate **Division OU**.

   b. Select **Allow users** in this OU to access the Cornerstone Learn app on their mobile and tablet device and checkbox in Enable Mobile Access.

   c. Select **Save**.
3. Open **Cornerstone Learn** mobile application. On the sign in page, enter the portal name.

   ![Screenshot for mobile application Cornerstone.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cornerstone-ondemand-tutorial/welcome-mobile.png)

4. Select **Alternative Login** and then select **SSO**.

   ![Screenshot for mobile application Alternative Login.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cornerstone-ondemand-tutorial/sso-mobile.png)

5. . Enter your **Microsoft Entra credentials** to sign into the Cornerstone application and select **Next**.

   ![Screenshot for mobile application Microsoft Entra credentials.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cornerstone-ondemand-tutorial/credentials-mobile.png)

6. Finally after successful sign in, the application homepage is displayed as shown below.

   ![Screenshot of mobile application home page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/cornerstone-ondemand-tutorial/home-page-mobile.png)

## Related content

Once you configure Cornerstone Single Sign-On you can enforce Session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
