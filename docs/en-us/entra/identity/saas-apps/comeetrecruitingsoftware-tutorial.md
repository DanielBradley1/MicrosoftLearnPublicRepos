<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/comeetrecruitingsoftware-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure Comeet Recruiting Software for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate Comeet Recruiting Software with Microsoft Entra ID. When you integrate Comeet Recruiting Software with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to Comeet Recruiting Software.
- Enable your users to be automatically signed-in to Comeet Recruiting Software with their Microsoft Entra accounts.
- Manage your accounts in one central location.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- Comeet Recruiting Software single sign-on \(SSO\) enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

- Comeet Recruiting Software supports **SP and IDP** initiated SSO.
- Comeet Recruiting Software supports [Automated user provisioning](https://learn.microsoft.com/en-us/entra/identity/saas-apps/comeet-recruiting-software-provisioning-tutorial).

## Add Comeet Recruiting Software from the gallery

To configure the integration of Comeet Recruiting Software into Microsoft Entra ID, you need to add Comeet Recruiting Software from the gallery to your list of managed SaaS apps.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Comeet Recruiting Software** in the search box.
4. Select **Comeet Recruiting Software** from results panel and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides).

## Configure and test Microsoft Entra SSO for Comeet Recruiting Software

Configure and test Microsoft Entra SSO with Comeet Recruiting Software using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in Comeet Recruiting Software.

To configure and test Microsoft Entra SSO with Comeet Recruiting Software, perform the following steps:

1. **[Configure Microsoft Entra SSO](#configure-azure-ad-sso)** - to enable your users to use this feature.

   1. **Create a Microsoft Entra test user** - to test Microsoft Entra single sign-on with Britta Simon.
   2. **Assign the Microsoft Entra test user** - to enable Britta Simon to use Microsoft Entra single sign-on.

2. **[Configure Comeet Recruiting Software SSO](#configure-comeet-recruiting-software-sso)** - to configure the Single Sign-On settings on application side.

   1. **[Create Comeet Recruiting Software test user](#create-comeet-recruiting-software-test-user)** - to have a counterpart of Britta Simon in Comeet Recruiting Software that's linked to the Microsoft Entra representation of user.

3. **[Test SSO](#test-sso)** - to verify whether the configuration works.

## Configure Microsoft Entra SSO

Follow these steps to enable Microsoft Entra SSO.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Comeet Recruiting Software** > **Single sign-on**.
3. On the **Select a single sign-on method** page, select **SAML**.
4. On the **Set up single sign-on with SAML** page, select the pencil icon for **Basic SAML Configuration** to edit the settings.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. On the **Basic SAML Configuration** section, If you wish to configure the application in **IDP** initiated mode, perform the following steps:

   a. In the **Identifier** text box, type a URL using the following pattern: `https://app.comeet.co/adfs_auth/acs/<UNIQUEID>/`

   b. In the **Reply URL** text box, type a URL using the following pattern: `https://app.comeet.co/adfs_auth/acs/<UNIQUEID>/`

   Note

   These values aren't real. Update these values with the actual Identifier, and Reply URL. Contact [Comeet Recruiting Software Client support team](https://support.comeet.co/knowledgebase/adfs-single-sign-on/) to get these values. You can also refer to the patterns shown in the **Basic SAML Configuration** section.
6. Select **Set additional URLs** and perform the following step if you wish to configure the application in **SP** initiated mode:

   In the **Sign-on URL** text box, type a URL: `https://app.comeet.co`
7. Comeet Recruiting Software application expects the SAML assertions in a specific format. Configure the following claims for this application. You can manage the values of these attributes from the **User Attributes** section on application integration page. On the **Set up Single Sign-On with SAML** page, select **Edit** button to open **User Attributes** dialog.

   ![Screenshot that shows the "User Attributes" section with the "Edit" button selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-attribute.png)

8. In the **User Claims** section on the **User Attributes** dialog, edit the claims by using **Edit icon** or add the claims by using **Add new claim** to configure SAML token attribute as shown in the image above and perform the following steps:
   | Name | Source Attribute |
   | --- | --- |
   | nameidentifier | user.mail |
   | comeet\_id | user.userprincipalname |


   a. Select **Add new claim** to open the **Manage user claims** dialog.


   ![Screenshot that shows the "User claims" section with the "Add new claim" and "Save" actions highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/new-save-attribute.png)


   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/new-attribute-details.png)


   b. In the **Name** textbox, type the attribute name shown for that row.


   c. Leave the **Namespace** blank.


   d. Select Source as **Attribute**.


   e. From the **Source attribute** list, type the attribute value shown for that row.


   f. Select **Ok**


   g. Select **Save**.

9. On the **Set up Single Sign-On with SAML** page, in the **SAML Signing Certificate** section, select **Download** to download the **Federation Metadata XML** from the given options as per your requirement and save it on your computer.

   ![The Certificate download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

10. On the **Set up Comeet Recruiting Software** section, copy the appropriate URL\(s\) as per your requirement.

    ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure Comeet Recruiting Software SSO

To configure single sign-on on **Comeet Recruiting Software** side, you need to send the downloaded **Federation Metadata XML** and appropriate copied URLs from the application configuration to [Comeet Recruiting Software support team](https://support.comeet.co/knowledgebase/adfs-single-sign-on/). They set this setting to have the SAML SSO connection set properly on both sides.

### Create Comeet Recruiting Software test user

In this section, you create a user called Britta Simon in Comeet Recruiting Software. Work with [Comeet Recruiting Software support team](mailto:support@comeet.co) to add the users in the Comeet Recruiting Software platform. Users must be created and activated before you use single sign-on.

Comeet Recruiting Software also supports automatic user provisioning, you can find more details [here](https://learn.microsoft.com/en-us/entra/identity/saas-apps/comeet-recruiting-software-provisioning-tutorial) on how to configure automatic user provisioning.

### Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

SP initiated:

- Select **Test this application**, this option redirects to Comeet Recruiting Software Sign on URL where you can initiate the login flow.
- Go to Comeet Recruiting Software Sign-on URL directly and initiate the login flow from there.

IDP initiated:

- Select **Test this application**, and you should be automatically signed in to the Comeet Recruiting Software for which you set up the SSO

You can also use Microsoft My Apps to test the application in any mode. When you select the Comeet Recruiting Software tile in the My Apps, if configured in SP mode you would be redirected to the application sign on page for initiating the login flow and if configured in IDP mode, you should be automatically signed in to the Comeet Recruiting Software for which you set up the SSO. For more information, see [Microsoft Entra My Apps](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/end-user-experiences#azure-ad-my-apps).

## Related content

Once you configure Comeet Recruiting Software you can enforce session control, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session control extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-any-app).
