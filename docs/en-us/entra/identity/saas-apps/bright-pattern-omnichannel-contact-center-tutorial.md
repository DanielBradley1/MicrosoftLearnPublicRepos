<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/bright-pattern-omnichannel-contact-center-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure Bright Pattern Omnichannel Contact Center for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Bright Pattern Omnichannel Contact Center with Microsoft Entra ID. When you integrate Bright Pattern Omnichannel Contact Center with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Bright Pattern Omnichannel Contact Center.
- Enable your users to be automatically signed-in to Bright Pattern Omnichannel Contact Center with their Microsoft Entra accounts.
- Manage your accounts in one central location.

To learn more about SaaS app integration with Microsoft Entra ID, see [What is application access and single sign-on with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Bright Pattern Omnichannel Contact Center single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Bright Pattern Omnichannel Contact Center supports **SP and IDP** initiated SSO
- Bright Pattern Omnichannel Contact Center supports **Just In Time** user provisioning

## Adding Bright Pattern Omnichannel Contact Center from the gallery

To configure the integration of Bright Pattern Omnichannel Contact Center into Microsoft Entra ID, you need to add Bright Pattern Omnichannel Contact Center from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Bright Pattern Omnichannel Contact Center** in the search box.
4. Select **Bright Pattern Omnichannel Contact Center** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra single sign-on for Bright Pattern Omnichannel Contact Center

Configure and test Microsoft Entra SSO with Bright Pattern Omnichannel Contact Center using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Bright Pattern Omnichannel Contact Center.

To configure and test Microsoft Entra SSO with Bright Pattern Omnichannel Contact Center, complete the following building blocks:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Bright Pattern Omnichannel Contact Center SSO](#configure-bright-pattern-omnichannel-contact-center-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Bright Pattern Omnichannel Contact Center test user](#create-bright-pattern-omnichannel-contact-center-test-user)** - to have a counterpart of B.Simon in Bright Pattern Omnichannel Contact Center that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Bright Pattern Omnichannel Contact Center** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the edit/pen icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, enter the values for the following fields:

   a. In the **Identifier** text box, type a URL using the following pattern: `<SUBDOMAIN>_sso`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.brightpattern.com/agentdesktop/sso/redirect`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL using the following pattern: `https://<SUBDOMAIN>.brightpattern.com/`

   Note

   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign-on URL. Contact [Bright Pattern Omnichannel Contact Center Client support team](mailto:support@brightpattern.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. Bright Pattern Omnichannel Contact Center application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-attribute.png)

8. In addition to above, Bright Pattern Omnichannel Contact Center application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirement.
   | Name | Namespace |
   | --- | --- |
   | firstName | user.givenname |
   | lastName | user.surname |
   | email | user.mail |
9. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

10. On the **Set up Bright Pattern Omnichannel Contact Center** section, copy the appropriate URL\(s\) based on your requirement.

    ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Bright Pattern Omnichannel Contact Center SSO

To configure single sign-on on **Bright Pattern Omnichannel Contact Center** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Bright Pattern Omnichannel Contact Center support team](mailto:support@brightpattern.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Bright Pattern Omnichannel Contact Center test user

In this section, a user called B.Simon is created in Bright Pattern Omnichannel Contact Center. Bright Pattern Omnichannel Contact Center supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Bright Pattern Omnichannel Contact Center, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration using the Access Panel.

When you select the Bright Pattern Omnichannel Contact Center tile in the Access Panel, you should be automatically signed in to the Bright Pattern Omnichannel Contact Center for which you set up SSO. For more information about the Access Panel, see [Introduction to the Access Panel](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Additional resources

- [List of articles on How to Integrate SaaS Apps with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)
