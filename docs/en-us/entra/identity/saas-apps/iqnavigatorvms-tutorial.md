<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/iqnavigatorvms-tutorial -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Configure IQNavigator VMS for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate IQNavigator VMS with Microsoft Entra ID. When you integrate IQNavigator VMS with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to IQNavigator VMS.
- Enable your users to be automatically signed-in to IQNavigator VMS with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- IQNavigator VMS single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- IQNavigator VMS supports **IDP** initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add IQNavigator VMS from the gallery

To configure the integration of IQNavigator VMS into Microsoft Entra ID, you need to add IQNavigator VMS from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **IQNavigator VMS** in the search box.
4. Select **IQNavigator VMS** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for IQNavigator VMS

Configure and test Microsoft Entra SSO with IQNavigator VMS using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in IQNavigator VMS.

To configure and test Microsoft Entra SSO with IQNavigator VMS, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure IQNavigator VMS SSO](#configure-iqnavigator-vms-sso)** - to configure the single sign-on settings on application side.

   1. **[Create IQNavigator VMS test user](#create-iqnavigator-vms-test-user)** - to have a counterpart of B.Simon in IQNavigator VMS that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **IQNavigator VMS** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type the value: `iqn.com`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://<subdomain>.iqnavigator.com/security/login?client_name=https://sts.window.net/<instance name>`

   c. Select **Set additional URLs**.

   d. In the **Relay State** text box, type a URL using the following pattern: `https://<subdomain>.iqnavigator.com`

   Note

   These values aren't real. Update these values with the actual Reply URL and Relay State. Contact [IQNavigator VMS Client support team](https://www.beeline.com/contact-support/) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. IQNavigator application expect the Unique User Identifier value in the Name Identifier claim. Customer can map the correct value for the Name Identifier claim. In this case we have mapped the user.UserPrincipalName for the demo purpose. But according to your organization settings you should map the correct value for it.

   ![Screenshot shows the image of IQNavigator application.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-attribute.png "Image")

7. On the **Set up single sign-on with SAML** page, In the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure IQNavigator VMS SSO

To configure single sign-on on **IQNavigator VMS** side, you need to send the **App Federation Metadata Url** to [IQNavigator VMS support team](https://www.beeline.com/contact-support/). They set this setting to have the SAML SSO connection set properly on both sides.

### Create IQNavigator VMS test user

In this section, you create a user called Britta Simon in IQNavigator VMS. Work with [IQNavigator VMS support team](https://www.beeline.com/contact-support/) to add the users in the IQNavigator VMS platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the IQNavigator VMS for which you set up the SSO.
- You can use Microsoft My Apps. When you select the IQNavigator VMS tile in the My Apps, you should be automatically signed in to the IQNavigator VMS for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure IQNavigator VMS you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
