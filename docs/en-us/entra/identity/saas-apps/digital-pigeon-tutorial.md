<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/digital-pigeon-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Digital Pigeon for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Digital Pigeon with Microsoft Entra ID. Digital Pigeon helps creative people deliver their work, beautifully and quickly. Whatever your needs, Digital Pigeon makes sending and receiving large files seamless. When you integrate Digital Pigeon with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Digital Pigeon.
- Enable your users to be automatically signed-in to Digital Pigeon with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for Digital Pigeon in a test environment. Digital Pigeon supports both **SP** and **IDP** initiated single sign-on and also supports **Just In Time** user provisioning.

## Prerequisites

To integrate Microsoft Entra ID with Digital Pigeon, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Digital Pigeon single sign-on \(SSO\) enabled subscription \(that is, Business or Enterprise plans\)
- Digital Pigeon account owner access to the above subscription

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the Digital Pigeon application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add Digital Pigeon from the Microsoft Entra gallery

Add Digital Pigeon from the Microsoft Entra application gallery to configure single sign-on with Digital Pigeon. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Note

Please select [here](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps#app-roles-ui) to learn how to configure App Roles in Microsoft Entra ID. The Role value must be one of 'Digital Pigeon User', 'Digital Pigeon Power User', or 'Digital Pigeon Admin'. If a role claim isn't supplied, the default role is configurable in the Digital Pigeon app \(`Account Settings > SSO > SAML Provisioning Settings`\) by a Digital Pigeon Owner, as seen below: ![Screenshot shows how to configure SAML Provisioning Default Role.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/digital-pigeon-tutorial/saml-default-role.png "SAML Default Role")

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Digital Pigeon** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. In another browser tab, log in to Digital Pigeon as an account administrator.
6. Navigate to **Account Settings > SSO** and copy the **SP Entity ID** and **SP ACS URL** values.

   ![Screenshot shows Digital Pigeon SAML Service Provider Settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/digital-pigeon-tutorial/saml-service-provider-settings.png "SAML Service Provider Settings")

7. Now in Microsoft Entra ID, in the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, paste the value from *Digital Pigeon > Account Settings > SSO > **SP Entity ID***. It should match the following pattern: `https://digitalpigeon.com/saml2/service-provider-metadata/<CustomerID>`

   b. In the **Reply URL** textbox, paste the value from *Digital Pigeon > Account Settings > SSO > **SP ACS URL***. It should match the following pattern: `https://digitalpigeon.com/login/saml2/sso/<CustomerID>`
8. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign on URL** textbox, type the URL: `https://digitalpigeon.com/login`
9. Digital Pigeon application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Attributes")

10. In addition to above, Digital Pigeon application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
    | Name | Source Attribute |
    | --- | --- |
    | user.firstName | user.givenname |
    | user.lastName | user.surname |
11. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

    ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

12. In Digital Pigeon, paste the content of downloaded **Federation Metadata XML** file into the **IDP Metadata XML** text field.

    ![Screenshot shows IDP Metadata XML.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/digital-pigeon-tutorial/idp-metadata-xml.png "IDP Metadata XML")

13. In Microsoft Entra ID, on the **Set up Digital Pigeon** section, copy the Microsoft Entra Identifier URL.

    ![Screenshot shows to copy configuration appropriate U R L.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

14. In Digital Pigeon, paste this URL into the **IDP Entity ID** text field.

    ![Screenshot shows IDP Entity ID.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/digital-pigeon-tutorial/idp-entity-id.png "IDP Entity ID")

15. Select **Save** button to activate Digital Pigeon SSO.

### Create Digital Pigeon test user

In this section, a user called B.Simon is created in Digital Pigeon. Digital Pigeon supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Digital Pigeon, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to Digital Pigeon Sign on URL where you can initiate the login flow.
- Go to Digital Pigeon Sign on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Digital Pigeon for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the Digital Pigeon tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Digital Pigeon for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- Should you run into any issues or require additional support, please contact the [Digital Pigeon support team](mailto:help@digitalpigeon.com)
- For an alternative step-by-step guide, please refer to the Digital Pigeon KB article: [Microsoft Entra SSO Configuration](https://digitalpigeon.zendesk.com/hc/en-us/articles/5403612403855-Azure-AD-SSO-Configuration)
- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure Digital Pigeon you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
