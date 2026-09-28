<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/roadmunk-tutorial -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Configure Roadmunk for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Roadmunk with Microsoft Entra ID. When you integrate Roadmunk with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Roadmunk.
- Enable your users to be automatically signed in to Roadmunk by using their Microsoft Entra accounts.
- Manage your accounts in one central location, the Azure portal.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A Roadmunk subscription that's enabled for single sign-on \(SSO\).

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

Roadmunk supports SSO that's started by the *service provider* \(SP\) and by the *identity provider \(IDP\)*.

## Add Roadmunk from the gallery

To integrate Roadmunk into Microsoft Entra ID, from the gallery, add Roadmunk to your list of managed SaaS apps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, in the search box, type **Roadmunk**.
4. Select **Roadmunk** from the results, and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for Roadmunk

Configure and test Microsoft Entra SSO with Roadmunk by using a test user called *B.Simon*. To make SSO work, you need to establish a link relationship between a Microsoft Entra user and the related user in Roadmunk.

Here's an overview of how to configure and test Microsoft Entra SSO with Roadmunk:

1. [Configure Microsoft Entra SSO](#configure-azure-ad-sso) so that your users can use this feature.

   1. Create a Microsoft Entra test user to test Microsoft Entra SSO by using B.Simon.
   2. Assign the Microsoft Entra test user to enable B.Simon to use Microsoft Entra SSO.

2. [Configure Roadmunk SSO](#configure-roadmunk-sso) to configure the SSO settings on the application side.

   1. [Create a Roadmunk test user](#create-roadmunk-test-user) so that you can link the counterpart of B.Simon in Roadmunk to the Microsoft Entra representation of the user.

3. [Test SSO](#test-sso) to make sure the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO in the Azure portal:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Roadmunk** application integration page, find the **Manage** section, and then select **single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pen icon for **Basic SAML Configuration** to edit the settings.

   ![Screenshot showing the Edit icon for Basic SAML Configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, if you have an SP metadata file and you want to configure in IDP-initiated mode, follow these steps:

   a. Select **Upload metadata file**.

   ![Screenshot showing the link for Upload metadata file.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/upload-metadata.png)


   b. Select the folder icon to choose the metadata file that you downloaded in step 4 of the "Configure Roadmunk SSO" procedure. Then select **Upload**.


   ![Screenshot showing how to choose the metadata file.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/browse-upload-metadata.png)


   After the metadata file is uploaded, in the **Basic SAML Configuration** section, the **Identifier** and **Reply URL** values are automatically populated.


   ![Screenshot showing the Basic SAML Configuration section. The Identifier field and the Reply URL field are highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/idp-intiated.png)


   Note


   If the **Identifier** and **Reply URL** values aren't automatically populated, then fill in the values manually.

6. If you want to configure the application in SP-initiated mode, select **Set additional URLs**. In the **Sign-on URL** field, type `https://login.roadmunk.com`

   ![Screenshot showing where to set a sign-on URL for SP-initiated mode.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadata-upload-additional-signon.png)

7. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Federation Metadata XML**. Then select **Download** to download the certificate and save it on your computer.

   ![Screenshot showing the download link for the SAML signing certificate.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

8. In the **Set up Roadmunk** section, copy the URL or URLs that you need.

   ![Screenshot showing where to copy configuration URLs.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Roadmunk SSO

1. Sign in to the Roadmunk website as an administrator.
2. At the bottom of the page, select the user icon, and then select **Account Settings**.

   ![Screenshot showing where to select user account settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/roadmunk-tutorial/account.png)

3. Go to **Company** > **Authentication Settings**.
4. On the **Authentication Settings** page, follow these steps:

   ![Screenshot showing the Authentication Settings page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/roadmunk-tutorial/saml-sso.png)


   a. Turn on **SAML Single Sign On \(SSO\)**.


   b. In the **Step 1** section, either upload the metadata XML file or provide the URL for the metadata.


   c. In the **Step 2** section, download the Roadmunk Metadata file, and then save it on your computer.


   d. If you want to sign in by using SSO, in the **Step 3** section, select **Enforce SAML Sign-In Only**.


   e. Select **Save**.

### Create Roadmunk test user

1. Sign in to the Roadmunk website as an administrator.
2. Select the user icon at the bottom of the page, and then select **Account Settings**.

   ![Screenshot showing how to open Account Settings for the test user.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/roadmunk-tutorial/account.png)

3. Open the **Users** tab, and then select **Invite User**.

   ![Screenshot showing the Users tab. The Invite User button is highlighted. In the open window, the Email and Role fields are highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/roadmunk-tutorial/create-user.png)

4. In the form that appears, fill in the required information, and then select **Invite**.

## Test SSO

In this section, you test your Microsoft Entra SSO configuration by using the access panel.

In the My Apps portal, when you select the **Roadmunk** tile, you should be automatically signed in to the Roadmunk account for which you set up SSO. For more information, see [Sign in and start apps from the My Apps portal](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

After you configure Roadmunk, you can enforce session control. Session control protects the exfiltration and infiltration of your organization's sensitive data in real time. Session control extends from Conditional Access.

Learn how to [enforce session control by using Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
