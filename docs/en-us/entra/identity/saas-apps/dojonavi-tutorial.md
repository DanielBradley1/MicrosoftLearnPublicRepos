<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/dojonavi-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure DojoNavi for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate DojoNavi with Microsoft Entra ID. "Dojo Navi" is a next-generation manual solution that greatly contributes to various system operations in a company by providing "navigation functions" and "blocking functions" in system operation that have never existed before, in order to significantly improve system operation efficiency and significantly reduce system operation costs. When you integrate DojoNavi with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to DojoNavi.
- Enable your users to be automatically signed-in to DojoNavi with their Microsoft Entra accounts.
- Manage your accounts in one central location.

You'll configure and test Microsoft Entra single sign-on for DojoNavi in a test environment. DojoNavi supports **SP** and **IDP** initiated single sign-on.

## Prerequisites

To integrate Microsoft Entra ID with DojoNavi, you need:

- A Microsoft Entra user account. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Microsoft Entra subscription. If you don't have a subscription, you can get a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- DojoNavi single sign-on \(SSO\) enabled subscription.

## Add application and assign a test user

Before you begin the process of configuring single sign-on, you need to add the DojoNavi application from the Microsoft Entra gallery. You need a test user account to assign to the application and test the single sign-on configuration.

### Add DojoNavi from the Microsoft Entra gallery

Add DojoNavi from the Microsoft Entra application gallery to configure single sign-on with DojoNavi. For more information on how to add application from the gallery, see the [Quickstart: Add application from the gallery](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) article to create a test user account called B.Simon.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, and assign roles. The wizard also provides a link to the single sign-on configuration pane. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure Microsoft Entra SSO

Complete the following steps to enable Microsoft Entra single sign-on.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **DojoNavi** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot shows how to edit Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png "Basic Configuration")

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Identifier** textbox, type a URL using one of the following patterns:

   | **Identifier** |
   | --- |
   | `https://<SUBDOMAIN>.dojo-navi.com/external_sso_service/metadata/` |
   | `https://<SUBDOMAIN>.dojo-sero.tepss.com/external_sso_service/metadata/` |


   b. In the **Reply URL** textbox, type a URL using one of the following patterns:


   | **Reply URL** |
   | --- |
   | `https://<SUBDOMAIN>.dojo-navi.com/external_sso_service/acs/` |
   | `https://<SUBDOMAIN>.dojo-sero.tepss.com/external_sso_service/acs/` |

6. If you wish to configure the application in **SP** initiated mode, then perform the following step:

   In the **Sign on URL** textbox, type a URL using one of the following patterns:

   | **Sign on URL** |
   | --- |
   | `https://<SUBDOMAIN>.dojo-navi.com/external_sso_service/sso/` |
   | `https://<SUBDOMAIN>.dojo-sero.tepss.com/external_sso_service/sso/` |


   Note


   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact [DojoNavi Client support team](mailto:product_support@tenda.co.jp) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

7. On the **Set-up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![Screenshot shows the Certificate download link.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png "Certificate")

8. On the **Set up DojoNavi** section, copy the appropriate URL\(s\) based on your requirement.

   ![Screenshot shows to copy configuration appropriate URL.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png "Metadata")

## Configure DojoNavi SSO

To configure single sign-on on **DojoNavi** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [DojoNavi support team](mailto:product_support@tenda.co.jp). They set this setting to have the SAML SSO connection set properly on both sides.

### Create DojoNavi test user

In this section, you create a user called Britta Simon at DojoNavi. Work with [DojoNavi support team](mailto:product_support@tenda.co.jp) to add the users in the DojoNavi platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to DojoNavi Sign-on URL where you can initiate the login flow.
- Go to DojoNavi Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the DojoNavi for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the DojoNavi tile in the My Apps, if configured in SP mode you would be redirected to the application sign-on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the DojoNavi for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Additional resources

- [What is single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Plan a single sign-on deployment](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment).

## Related content

Once you configure DojoNavi you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Cloud App Security](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
