<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/ns1-sso-azure-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure NS1 SSO for Azure for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate NS1 SSO for Azure with Microsoft Entra ID. When you integrate NS1 SSO for Azure with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to NS1 SSO for Azure.
- Enable your users to be automatically signed in to NS1 SSO for Azure with their Microsoft Entra accounts.
- Manage your accounts in one central location, the Azure portal.

## Prerequisites

To get started, you need the following items:

- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- NS1 SSO for Azure single sign-on \(SSO\) enabled subscription.
- Along with Cloud Application Administrator, Application Administrator can also add or manage applications in Microsoft Entra ID. For more information, see [Azure built-in roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- NS1 SSO for Azure supports SP and IDP initiated SSO.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Add NS1 SSO for Azure from the gallery

To configure the integration of NS1 SSO for Azure into Microsoft Entra ID, you need to add NS1 SSO for Azure from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **NS1 SSO for Azure** in the search box.
4. Select **NS1 SSO for Azure** from the results panel, and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for NS1 SSO for Azure

Configure and test Microsoft Entra SSO with NS1 SSO for Azure by using a test user called **B.Simon**. For SSO to work, establish a linked relationship between a Microsoft Entra user and the related user in NS1 SSO for Azure.

Here are the general steps to configure and test Microsoft Entra SSO with NS1 SSO for Azure:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** to enable your users to use this feature.

   a. **Create a Microsoft Entra test user** to test Microsoft Entra single sign-on with B.Simon.

   b. **Assign the Microsoft Entra test user** to enable B.Simon to use Microsoft Entra single sign-on.
2. **[Configure NS1 SSO for Azure SSO](#configure-ns1-sso-for-azure-sso)** to configure the single sign-on settings on the application side.

   a. **[Create an NS1 SSO for Azure test user](#create-an-ns1-sso-for-azure-test-user)** to have a counterpart of B.Simon in NS1 SSO for Azure. This counterpart is linked to the Microsoft Entra representation of the user.
3. **[Test SSO](#test-sso)** to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **NS1 SSO for Azure** application integration page, find the **Manage** section. Select **single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot of set up single sign-on with SAML page, with pencil icon highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** text box, type the following URL: `https://api.nsone.net/saml/metadata`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://api.nsone.net/saml/sso/<ssoid>`
6. Select **Set additional URLs**, and perform the following step if you want to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type the following URL: `https://my.nsone.net/#/login/sso`

   Note

   The Reply URL value isn't real. Update Reply URL value with the actual Reply URL. Contact the [NS1 SSO for Azure Client support team](mailto:techops@nsone.net) to get the value. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. The NS1 SSO for Azure application expects the SAML assertions in a specific format. Configure the following claims for this application. You can manage the values of these attributes from the **User Attributes & Claims** section on the application integration page. On the **Set up Single Sign-On with SAML** page, select the pencil icon to open the **User Attributes** dialog box.

   ![Screenshot of User Attributes & Claims section, with pencil icon highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ns1-sso-for-azure-tutorial/attribute-edit-option.png)

8. Select the attribute name to edit the claim.

   ![Screenshot of User Attributes & Claims section, with attribute name highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ns1-sso-for-azure-tutorial/attribute-claim-edit.png)

9. Select **Transformation**.

   ![Screenshot of Manage claim section, with Transformation highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ns1-sso-for-azure-tutorial/prefix-edit.png)

10. In the **Manage transformation** section, perform the following steps:

    ![Screenshot of Manage transformation section, with various fields highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/ns1-sso-for-azure-tutorial/prefix-added.png)


    1. Select **ExactMailPrefix\(\)** as **Transformation**.
    2. Select **user.userprincipalname** as **Parameter 1**.
    3. Select **Add**.
    4. Select **Save**.

11. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select the copy button. This copies the **App Federation Metadata Url** and saves it on your computer.

    ![Screenshot of the SAML Signing Certificate, with the copy button highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure NS1 SSO for Azure SSO

To configure single sign-on on the NS1 SSO for Azure side, you need to send the App Federation Metadata URL to the [NS1 SSO for Azure support team](mailto:techops@nsone.net). They configure this setting to have the SAML SSO connection set properly on both sides.

### Create an NS1 SSO for Azure test user

In this section, you create a user called B.Simon in NS1 SSO for Azure. Work with the NS1 SSO for Azure support team to add the users in the NS1 SSO for Azure platform. You can't use single sign-on until you create and activate users.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to NS1 SSO for Azure Sign-on URL where you can initiate the login flow.
- Go to NS1 SSO for Azure Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the NS1 SSO for Azure for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the NS1 SSO for Azure tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the NS1 SSO for Azure for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure NS1 SSO for Azure you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
