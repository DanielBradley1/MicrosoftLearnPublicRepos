<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/wikispaces-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Wikispaces for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Wikispaces with Microsoft Entra ID. When you integrate Wikispaces with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Wikispaces.
- Enable your users to be automatically signed-in to Wikispaces with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

To configure Microsoft Entra integration with Wikispaces, you need the following items:

- A Microsoft Entra subscription. If you don't have a Microsoft Entra environment, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Wikispaces single sign-on enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra single sign-on in a test environment.

- Wikispaces supports **SP** initiated SSO.

## Add Wikispaces from the gallery

To configure the integration of Wikispaces into Microsoft Entra ID, you need to add Wikispaces from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Wikispaces** in the search box.
4. Select **Wikispaces** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Wikispaces

Configure and test Microsoft Entra SSO with Wikispaces using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Wikispaces.

To configure and test Microsoft Entra SSO with Wikispaces, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Wikispaces SSO](#configure-wikispaces-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Wikispaces test user](#create-wikispaces-test-user)** - to have a counterpart of B.Simon in Wikispaces that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Wikispaces** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic S A M L Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://session.wikispaces.net/<instancename>`

   b. In the **Sign on URL** text box, type a URL using the following pattern: `https://<companyname>.wikispaces.net`

   Note

   These values aren't real. Update these values with the actual Identifier and Sign on URL. Contact Wikispaces Client support team to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

7. On the **Set up Wikispaces** section, copy the appropriate URL\(s\) as per your requirement.

   ![Screenshot shows to copy configuration appropriate U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Wikispaces SSO

To configure single sign-on on **Wikispaces** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to Wikispaces support team. They set this setting to have the SAML SSO connection set properly on both sides.

### Create Wikispaces test user

In order to enable Microsoft Entra users to sign in to Wikispaces, they must be provisioned into Wikispaces. In the case of Wikispaces, provisioning is a manual task.

### To provision a user account, perform the following steps:

1. Sign in to your **Wikispaces** company site as an administrator.
2. Go to **Members**.

   ![Screenshot shows the Members Menu.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/wikispaces-tutorial/profile.png "Members")

3. Select the **Invite People**.

   ![Screenshot shows the Members page where you can select Invite People.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/wikispaces-tutorial/menu.png "Invite People")

4. In the **Invite People** section, perform the following steps:

   ![Screenshot shows the Invite People section where you can enter user data.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/wikispaces-tutorial/user.png "People")


   a. Type the **Usernames or Email Address** of a valid Microsoft Entra account you want to provision into the related textboxes.


   b. Select **Send**.


   Note


   The Microsoft Entra account holder receives an email including a link to confirm the account before it becomes active.

Note

You can use any other Wikispaces user account creation tools or APIs provided by Wikispaces to provision Microsoft Entra user accounts.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Wikispaces Sign-on URL where you can initiate the login flow.
- Go to Wikispaces Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Wikispaces tile in the My Apps, this option redirects to Wikispaces Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Wikispaces you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
