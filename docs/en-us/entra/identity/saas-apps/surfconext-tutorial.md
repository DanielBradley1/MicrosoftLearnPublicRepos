<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/surfconext-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure SURFconext for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate SURFconext with Microsoft Entra ID. SURF connected institutions can use SURFconext to log in to many cloud applications with their institution credentials. When you integrate SURFconext with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to SURFconext.
- Enable your users to be automatically signed-in to SURFconext with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for SURFconext in a test environment. SURFconext supports **SP** initiated single sign-on and **Just In Time** user provisioning.

Note

Identifier of this application is a fixed string value so only one instance can be configured in one tenant.

## Prerequisites

To integrate Microsoft Entra ID with SURFconext, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- SURFconext single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the SURFconext application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add SURFconext from the Microsoft Entra gallery

Add SURFconext from the Microsoft Entra application gallery to configure single sign-on with SURFconext. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **SURFconext** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type one of the following URLs:

   | Environment | URL |
   | --- | --- |
   | Production | `https://engine.surfconext.nl/authentication/sp/metadata` |
   | Staging | `https://engine.test.surfconext.nl/authentication/sp/metadata` |


   b. In the **Reply URL** textbox, type one of the following URLs:


   | Environment | URL |
   | --- | --- |
   | Production | `https://engine.surfconext.nl/authentication/sp/consume-assertion` |
   | Staging | `https://engine.test.surfconext.nl/authentication/sp/consume-assertion` |


   c. In the **Sign on URL** textbox, type one of the following URLs:


   | Environment | URL |
   | --- | --- |
   | Production | `https://engine.surfconext.nl/authentication/sp/debug` |
   | Staging | `https://engine.test.surfconext.nl/authentication/sp/debug` |

6. SURFconext application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![Screenshot shows the image of attributes configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png "Image")


   Note


   You can remove or delete these default attributes manually under Additional claims section, if it isn't required.

7. In addition to above, SURFconext application expects few more attributes to be passed back in SAML response, which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | urn:mace:dir:attribute-def:cn | user.displayname |
   | urn:mace:dir:attribute-def:displayName | user.displayname |
   | urn:mace:dir:attribute-def:eduPersonPrincipalName | user.userprincipalname |
   | urn:mace:dir:attribute-def:givenName | user.givenname |
   | urn:mace:dir:attribute-def:mail | user.mail |
   | urn:mace:dir:attribute-def:preferredLanguage | user.preferredlanguage |
   | urn:mace:dir:attribute-def:sn | user.surname |
   | urn:mace:dir:attribute-def:uid | user.userprincipalname |
   | urn:mace:terena.org:attribute-def:schacHomeOrganization | user.userprincipalname |
8. To perform Transform operation for **urn:mace:terena.org:attribute-def:schacHomeOrganization** claim, select **Transformation** button as a Source under **Manage claim** section.
9. In the **Manage transformation** page, perform the following steps:

   ![Screenshot shows the Azure portal attributes.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/surfconext-tutorial/transform.png "Admin")


   1. Select **Extract\(\)** from the dropdown in **Transformation** field and select **After matching** button.
   2. Select **Attribute** as a **Parameter 1 \(Input\)**.
   3. In the **Attribute name** field, select **user.userprinciplename** from the dropdown.
   4. Select **@** value from the dropdown.
   5. Select **Add**.

10. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, select copy button to copy **App Federation Metadata Url** and save it on your computer.

    ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-metadataurl.png "Certificate")

## Configure SURFconext SSO

To configure single sign-on on **SURFconext** side, you need to send the **App Federation Metadata Url** to [SURFconext support team](mailto:support@surfconext.nl). They set this setting to have the SAML SSO connection set properly on both sides.

### Create SURFconext test user

In this section, a user called B.Simon is created in SURFconext. SURFconext supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in SURFconext, a new one is commonly created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to SURFconext Sign-on URL where you can initiate the login flow.
- Go to SURFconext Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the SURFconext tile in the My Apps, this option redirects to SURFconext Sign-on URL. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure SURFconext you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
