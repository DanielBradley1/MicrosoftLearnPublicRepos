<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/fabric-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Fabric for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Fabric with Microsoft Entra ID. When you integrate Fabric with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Fabric.
- Enable your users to be automatically signed-in to Fabric with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Fabric single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Fabric supports **SP** initiated SSO.

## Adding Fabric from the gallery

To configure the integration of Fabric into Microsoft Entra ID, you need to add Fabric from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Fabric** in the search box.
4. Select **Fabric** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Fabric

Configure and test Microsoft Entra SSO with Fabric using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Fabric.

To configure and test Microsoft Entra SSO with Fabric, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure Fabric SSO](#configure-fabric-sso)** - to configure the single sign-on settings on application side.

   1. **[Create Fabric roles](#create-fabric-roles)** - to have a counterpart of B.Simon in Fabric that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Fabric** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, enter the values for the following fields:

   1. In the **Identifier** text box, type a URL using the following pattern:  
      `https://<HOSTNAME>`
   2. In the **Reply URL** text box, type a URL using the following pattern:  
      `https://<HOSTNAME>:<PORT>/api/authenticate`
   3. In the **Sign on URL** text box, type a URL using the following pattern:  
      `https://<HOSTNAME>:<PORT>`


   Note


   These values aren't real. Update these values with the actual Identifier, Reply URL and Sign on URL. Contact K2View COE team to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.

6. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

7. In the **Set up Fabric** section, copy the appropriate URL\(s\) based on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

8. In the **Token encryption** section, select **Import Certificate** and upload the Fabric certificate file. Contact the K2View COE team to get it.

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Fabric SSO

To configure single sign-on on the **Fabric** side, send the downloaded **Certificate \(Base64\)** and the appropriate copied URLs to the K2View COE support team. The team configures the setting so that the SAML SSO connection is set properly on both sides.

For more information, see *Fabric SAML Configuration* and *Microsoft Entra SAML Setup Guide* in the [K2view Knowledge Base](https://support.k2view.com/knowledge-base.html).

### Create Fabric roles

Work with the K2View COE support team to set Fabric roles that are matched to the Microsoft Entra groups, and which are relevant to the users who are going to use Fabric. You'll provide the Fabric team the group IDs, because they are sent in the SAML response.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- In the Azure portal, select **Test this application**. You'll be redirected to the Fabric sign-on URL, where you can initiate the login flow.
- Go to the Fabric sign-on URL directly and initiate the login flow from there.
- You can use Microsoft My Apps. When you select the **Fabric** tile in the My Apps portal, you be redirected to the Fabric sign-on URL. For more information about the My Apps portal, see [Introduction to the My Apps portal](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure Fabric you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
