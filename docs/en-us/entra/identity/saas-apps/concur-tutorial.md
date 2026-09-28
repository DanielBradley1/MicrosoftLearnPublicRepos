<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/concur-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Concur for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Concur with Microsoft Entra ID. When you integrate Concur with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Concur.
- Enable your users to be automatically signed-in to Concur with their Microsoft Entra accounts.
- Manage your accounts in one central location.

Note

The guidance provided in this article doesn't cover the new **Manage Single Sign-On** offering that's available from SAP Concur as of mid 2019. This new self-service SSO offering relies on **IdP initiated** sign-in which the current gallery app doesn't allow, due to the **Sign on URL** not being optional. The **Sign on URL** must be empty for IdP initiated sign-in via MyApps portal to work as intended. For these reason you must start out with a custom non-gallery application to set up SSO when using the **Manage Single Sign-On** feature in SAP Concur.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Concur single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Concur supports **SP** initiated SSO.
- Concur supports **Just In Time** user provisioning.

## Adding Concur from the gallery

To configure the integration of Concur into Microsoft Entra ID, you need to add Concur from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Concur** in the search box.
4. Select **Concur** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Concur

Configure and test Microsoft Entra SSO with Concur using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Concur.

To configure and test Microsoft Entra SSO with Concur, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Concur SSO](#configure-concur-sso)** - to configure the Single Sign-On settings on application side.

   1. **[Create Concur test user](#create-concur-test-user)** - to have a counterpart of B.Simon in Concur that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Concur** application integration page, find the **Manage** section and select **Single sign-on**.
3. On the **Select a Single sign-on method** page, select **SAML**.
4. On the **Set up Single Sign-On with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, perform the following steps:

   a. In the **Sign on URL** text box, type a URL using the following pattern: `https://www.concursolutions.com/UI/SSO/<OrganizationId>`

   b. In the **Identifier \(Entity ID\)** text box, type a URL using the following pattern: `https://<customer-domain>.concursolutions.com`

   c. For **Reply URL**, enter one of the following URL pattern:

   | Reply URL |
   | --- |
   | `https://www.concursolutions.com/SAMLRedirector/SAMLReceiver.ashx` |
   | `https://<customer-domain>.concursolutions.com/<OrganizationId>` |
   | `https://<customer-domain>.concur.com` |
   | `https://<customer-domain>.concursolutions.com` |


   Note


   These values aren't real. Update these values with the actual Sign-on URL, Identifier and Reply URL. Contact Concur Client support team to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

7. On the **Set up Concur** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Concur SSO

To configure single sign-on on **Concur** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to Concur support team. They set this setting to have the SAML SSO connection set properly on both sides.

Note

The configuration of your Concur subscription for federated SSO via SAML is a separate task, which you must contact Concur Client support team to perform.

### Create Concur test user

In this section, a user called B.Simon is created in Concur. Concur supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in Concur, a new one is created after authentication.

Concur also supports automatic user provisioning via SAP Cloud Identity Services. For more information, see how to configure provisioning of users [from Microsoft Entra ID to SAP Cloud Identity Services](https://learn.microsoft.com/en-us/entra/identity/saas-apps/sap-cloud-platform-identity-authentication-provisioning-tutorial), and how to configure provisioning of users [from SAP Cloud Identity Services to SAP Concur](https://help.sap.com/docs/cloud-identity-services/cloud-identity-services/target-sap-concur).

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, this option redirects to Concur Sign-on URL where you can initiate the login flow.
- Go to Concur Sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the Concur tile in the My Apps, this option redirects to Concur Sign-on URL. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Concur you can enforce Session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
