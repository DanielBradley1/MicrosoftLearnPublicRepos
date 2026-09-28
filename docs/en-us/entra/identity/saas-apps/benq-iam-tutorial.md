<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/benq-iam-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure BenQ IAM for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate BenQ IAM with Microsoft Entra ID. When you integrate BenQ IAM with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to BenQ IAM.
- Enable your users to be automatically signed-in to BenQ IAM with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- BenQ IAM single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- BenQ IAM supports **SP and IDP** initiated SSO.

## Add BenQ IAM from the gallery

To configure the integration of BenQ IAM into Microsoft Entra ID, you need to add BenQ IAM from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **BenQ IAM** in the search box.
4. Select **BenQ IAM** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for BenQ IAM

Configure and test Microsoft Entra SSO with BenQ IAM using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in BenQ IAM.

To configure and test Microsoft Entra SSO with BenQ IAM, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with B.Simon.
   2. **Assign the Microsoft Entra test user** - to enable B.Simon to use Microsoft Entra single sign-on.

2. **[Configure BenQ IAM SSO](#configure-benq-iam-sso)** - to configure the single sign-on settings on application side.

   1. **[Create BenQ IAM test user](#create-benq-iam-test-user)** - to have a counterpart of B.Simon in BenQ IAM that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **BenQ IAM** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, if you wish to configure the application in **IDP** initiated mode, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://service-portal.benq.com/saml/init/<ID>`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://service-portal.benq.com/saml/consume/<ID>`
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Logout URL** text box, type the URL: `https://service-portal.benq.com/logout`

   Note

   These values aren't real. Update these values with the actual Identifier and Reply URL. Contact [BenQ IAM Client support team](mailto:benqcare.us@benq.com) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
7. BenQ IAM application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

8. In addition to above, BenQ IAM application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source Attribute |
   | --- | --- |
   | displayName | user.displayname |
   | externalId | user.objectid |
9. On the **Set up single sign-on with SAML** page, in the **SAML Signing Certificate** section, find **Certificate \(Base64\)** and select **Download** to download the certificate and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/certificatebase64.png)

10. On the **Set up BenQ IAM** section, copy the appropriate URL\(s\) based on your requirement.

    ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure BenQ IAM SSO

1. Login BenQ IAM with BenQ Admin Account, select **SSO Setting** in the Account Management section.

   ![Screenshot for SSO Setting](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/benq-iam-tutorial/sso-setting.png)

2. Under **SSO Setting**, select **SSO by SAML** and select **Next**.
3. Perform the following steps in the **SSO Setting** page.

   ![Screenshot for SSO configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/benq-iam-tutorial/saml-configuration.png)


   a. In the **Login/SSO URL** textbox, paste the **Login URL** value which you copied previously.


   b. In the **Identifier/Entity ID** textbox, paste the **Identifier** value which you copied previously.


   c. Open the downloaded **Certificate \(Base64\)** into Notepad and paste the content into the **Certificate\(Base64\)** textbox.


   d. Copy **Identifier** value, paste this value into the **Identifier** text box in the **Basic SAML Configuration** section.


   e. Copy **Reply URL** value, paste this value into the **Reply URL** text box in the **Basic SAML Configuration** section.


   f. Select **Next**.

### Create BenQ IAM test user

In this section, you create a user called Britta Simon in BenQ IAM. Work with [BenQ IAM support team](mailto:benqcare.us@benq.com) to add the users in the BenQ IAM platform. Users must be created and activated before you use single sign-on.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

#### SP initiated:

- Select **Test this application**, this option redirects to BenQ IAM Sign on URL where you can initiate the login flow.
- Go to BenQ IAM Sign-on URL directly and initiate the login flow from there.

#### IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the BenQ IAM for which you set up the SSO.

You can also use Microsoft My Apps to test the application in any mode. When you select the BenQ IAM tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the BenQ IAM for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure BenQ IAM you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
