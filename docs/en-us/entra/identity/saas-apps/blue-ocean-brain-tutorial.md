<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/blue-ocean-brain-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Blue Ocean Brain for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Blue Ocean Brain with Microsoft Entra ID. When you integrate Blue Ocean Brain with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Blue Ocean Brain.
- Enable your users to be automatically signed-in to Blue Ocean Brain with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Blue Ocean Brain single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Blue Ocean Brain supports **SP and IDP** initiated SSO.
- Blue Ocean Brain supports **Just In Time** user provisioning.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add Blue Ocean Brain from the gallery

To configure the integration of Blue Ocean Brain into Microsoft Entra ID, you need to add Blue Ocean Brain from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Blue Ocean Brain** in the search box.
4. Select **Blue Ocean Brain** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Blue Ocean Brain

Configure and test Microsoft Entra SSO with Blue Ocean Brain using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Blue Ocean Brain.

To configure and test Microsoft Entra SSO with Blue Ocean Brain, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Blue Ocean Brain SSO](#configure-blue-ocean-brain-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Blue Ocean Brain test user](#create-blue-ocean-brain-test-user)** - to have a counterpart of B.Simon in Blue Ocean Brain that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Blue Ocean Brain** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type the URL: `https://www3.blueoceanbrain.com`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://www3.blueoceanbrain.com/c/<friendly id>/saml/acs`

   c. In the **Sign-on URL** text box, type a URL using the following pattern: `https://www3.blueoceanbrain.com/c/<friendly id>/login`

   Note

   These values aren't real. Update these values with the actual Reply URL and Sign-on URL. Contact [Blue Ocean Brain Client support team](mailto:support@blueoceanbrain.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. Blue Ocean Brain application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

7. In addition to above, Blue Ocean Brain application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | FirstName | user.givenname |
   | LastName | user.surname |
   | Email | user.mail |
8. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Blue Ocean Brain SSO

To configure single sign-on on **Blue Ocean Brain** side, you need to send the **App Federation Metadata Url** to [Blue Ocean Brain support team](mailto:support@blueoceanbrain.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Blue Ocean Brain test user

In this section, a user called Britta Simon is created in Blue Ocean Brain. Blue Ocean Brain supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Blue Ocean Brain, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Blue Ocean Brain Sign on URL where you can initiate the login flow.
- Go to Blue Ocean Brain Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Blue Ocean Brain for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Blue Ocean Brain tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Blue Ocean Brain for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Blue Ocean Brain you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
