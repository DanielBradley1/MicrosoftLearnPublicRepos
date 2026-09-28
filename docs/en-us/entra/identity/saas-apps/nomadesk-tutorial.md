<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/nomadesk-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Nomadesk for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Nomadesk with Microsoft Entra ID. When you integrate Nomadesk with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Nomadesk.
- Enable your users to be automatically signed-in to Nomadesk with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Nomadesk single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Nomadesk supports **SP** initiated SSO.
- Nomadesk supports **Just In Time** user provisioning.

## Add Nomadesk from the gallery

To configure the integration of Nomadesk into Microsoft Entra ID, you need to add Nomadesk from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Nomadesk** in the search box.
4. Select **Nomadesk** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Nomadesk

Configure and test Microsoft Entra SSO with Nomadesk using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Nomadesk.

To configure and test Microsoft Entra SSO with Nomadesk, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Nomadesk SSO](#configure-nomadesk-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Nomadesk test user](#create-nomadesk-test-user)** - to have a counterpart of B.Simon in Nomadesk that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Nomadesk** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://secure.nomadesk.com/saml/<instancename>`

   b. In the **Sign on URL** text box, type a URL using the following pattern: `https://mynomadesk.com/logon/saml/<TENANTID>`

   Note

   These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact [Nomadesk Client support team](mailto:support@nomadesk.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Certificate \(Base64\)** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. On the **Set up Nomadesk** section, copy the appropriate URL\(s\) as per your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Nomadesk SSO

To configure single sign-on on **Nomadesk** side, you need to send the downloaded **Certificate \(Base64\)** and appropriate copied URLs from the application configuration to [Nomadesk support team](mailto:support@nomadesk.com). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Nomadesk test user

In this section, a user called Britta Simon is created in Nomadesk. Nomadesk supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Nomadesk, a new one is created after authentication.

Note

If you need to create a user manually, you need to contact the [Nomadesk support team](mailto:support@nomadesk.com).

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Nomadesk Sign-on URL where you can initiate the login flow.
- Go to Nomadesk Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Nomadesk tile in the My Apps, this option redirects to Nomadesk Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Nomadesk you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
