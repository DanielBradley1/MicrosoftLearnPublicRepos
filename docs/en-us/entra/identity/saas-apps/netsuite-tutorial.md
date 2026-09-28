<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/netsuite-tutorial -->
<!-- Sitemap-Last-Modified: 2025-03-25 -->

# Configure NetSuite for Single sign-on with Microsoft Entra ID

In this article, you learn how to integrate NetSuite with Microsoft Entra ID. When you integrate NetSuite with Microsoft Entra ID, you can:

- Control in Microsoft Entra ID who has access to NetSuite.
- Enable your users to be automatically signed in to NetSuite with their Microsoft Entra accounts.
- Manage your accounts in one central location, the Azure portal.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A NetSuite single sign-on \(SSO\)-enabled subscription.

## Scenario description

In this article, you configure and test Microsoft Entra SSO in a test environment.

NetSuite supports:

- IDP-initiated SSO.
- JIT \(just-in-time\) user provisioning.

Note

Because the identifier of this application is a fixed string value, only one instance can be configured in one tenant.

## Add NetSuite from the gallery

To configure the integration of NetSuite into Microsoft Entra ID, add NetSuite from the gallery to your list of managed SaaS apps by doing the following:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **NetSuite** in the search box.
4. In the results pane, select **NetSuite**, and then add the app. Wait a few seconds while the app is added to your tenant.

Alternatively, you can also use the [Enterprise App Configuration Wizard](https://portal.office.com/AdminPortal/home?Q=Docs#/azureadappintegration). In this wizard, you can add an application to your tenant, add users/groups to the app, assign roles, and walk through the SSO configuration as well. [Learn more about Microsoft 365 wizards.](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/azure-ad-setup-guides)

## Configure and test Microsoft Entra SSO for NetSuite

Configure and test Microsoft Entra SSO with NetSuite by using a test user called **B.Simon**. For SSO to work, you need to establish a link relationship between a Microsoft Entra user and the related user in NetSuite.

To configure and test Microsoft Entra SSO with NetSuite, perform the following steps:

1. [Configure Microsoft Entra SSO](#configure-azure-ad-sso) to enable your users to use this feature.

   - Create a Microsoft Entra test user to test Microsoft Entra single sign-on with user B.Simon.
   - Assign the Microsoft Entra test user to enable user B.Simon to use Microsoft Entra single sign-on.

2. [Configure NetSuite SSO](#configure-netsuite-sso) to configure the single sign-on settings on the application side.

   - [Create the NetSuite test user](#create-the-netsuite-test-user) to have a counterpart of user B.Simon in NetSuite that's linked to the Microsoft Entra representation of the user.

3. [Test SSO](#test-sso) to verify that the configuration works.

## Configure Microsoft Entra SSO

To enable Microsoft Entra SSO in the Azure portal, do the following:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **NetSuite** application integration page, look for the **Manage** section, and then select **Single sign-on**.
3. In the **Select a single sign-on method** pane, select **SAML**.
4. In the **Set up Single Sign-On with SAML** pane, select the **Edit** \("pencil"\) icon next to **Basic SAML Configuration**.

   ![Edit Basic SAML Configuration](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/edit-urls.png)

5. In the **Basic SAML Configuration** section, in the **Reply URL** text box, type the URL: `https://system.netsuite.com/saml2/acs`
6. NetSuite application expects the SAML assertions in a specific format, which requires you to add custom attribute mappings to your SAML token attributes configuration. The following screenshot shows the list of default attributes.

   ![image](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/default-attributes.png)

7. In addition to above, NetSuite application expects few more attributes to be passed back in SAML response which are shown below. These attributes are also pre populated but you can review them as per your requirements.
   | Name | Source attribute |
   | --- | --- |
   | account | `account id` |


   Note


   The value of the account attribute isn't real. You'll update this value, as explained later in this article.The account id isn't necessary unless you explicitly want to block the functionality of jumping from Production to the Sandbox in Netsuite within the navigation control.

8. On the Set up single sign-on with SAML page, in the SAML Signing Certificate section, find Federation Metadata XML and select Download to download the certificate and save it on your computer.

   ![The certificate Download link](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/metadataxml.png)

9. In the **Set up NetSuite** section, copy the appropriate URL or URLs, depending on your requirement.

   ![Copy configuration URLs](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/copy-configuration-urls.png)

### Create and assign Microsoft Entra test user

Follow the guidelines in the [create and assign a user account](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-assign-users) quickstart to create a test user account called B.Simon.

## Configure NetSuite SSO

1. Open a new tab in your browser, and sign in to your NetSuite company site as an administrator.
2. In the top navigation bar, select **Setup**, and then select **Company** > **Enable Features**.

   ![Screenshot shows Enable Features selected from Company.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-setupsaml.png)

3. In the toolbar at the middle of the page, select **SuiteCloud**.

   ![Screenshot shows SuiteCloud selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-suitecloud.png)

4. Under **Manage Authentication**, select the **SAML Single Sign-on** check box to enable the SAML single sign-on option in NetSuite.

   ![Screenshot shows Manage Authentication where you can select SAML Single Sign-on.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-ticksaml.png)

5. In the top navigation bar, select **Setup**.

   ![Screenshot shows Setup selected from the NETSUITE navigation bar.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-setup.png)

6. In the **Setup Tasks** list, select **Integration**.

   ![Screenshot shows Integration selected from SETUP TASKS.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-integration.png)

7. Under **Manage Authentication**, select **SAML Single Sign-on**.

   ![Screenshot show SAML Single Sign-on selected from the Integration item in SETUP TASKS.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-saml.png)

8. In the **SAML Setup** pane, under **NetSuite Configuration**, do the following:

   ![Screenshot shows SAML Setup where you can enter the values described.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-saml-setup.png)


   a. Select the **Primary Authentication Method** check box.


   b. Under **SAMLV2 Identity Provider Metadata**, select **Upload IDP Metadata File**, and then select **Browse** to upload the metadata file that you downloaded.


   c. Select **Submit**.

9. In the NetSuite top navigation bar, select **Setup**, and then select **Company** > **Company Information**.

   ![Screenshot shows Company Information selected from Company.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-com.png)


   ![Screenshot shows the pane where you can enter the values described.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-account-id.png)


   b. In the **Company Information** pane, in the right column, copy the **Account ID** value.


   c. Paste the **Account ID** that you copied from the NetSuite account into the **Attribute Value** box in Microsoft Entra ID.


   ![Screenshot shows to add the account id value](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/attribute-value.png)

10. Before users can perform single sign-on into NetSuite, they must first be assigned the appropriate permissions in NetSuite. To assign these permissions, do the following:

    a. In the top navigation bar, select **Setup**.

    ![Screenshot shows Setup selected from the NETSUITE navigation bar.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-setup.png)


    b. In the left pane, select **Users/Roles**, then select **Manage Roles**.


    ![Screenshot shows the Manage Roles pane where you can select New Role.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-manage-roles.png)


    c. Select **New Role**.


    d. Enter a **Name** for the new role.


    ![Screenshot shows the Setup Manager where you can enter a name for the role.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-new-role.png)


    e. Select **Save**.


    f. In the top navigation bar, select **Permissions**. Then select **Setup**.


    ![Screenshot shows the Setup tab where you can enter the values described.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-sso.png)


    g. Select **SAML Single Sign-on**, and then select **Add**.


    h. Select **Save**.


    i. In the top navigation bar, select **Setup**, and then select **Setup Manager**.


    ![Screenshot shows Setup selected from the NETSUITE navigation bar.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-setup.png)


    j. In the left pane, select **Users/Roles**, and then select **Manage Users**.


    ![Screenshot shows the Manage Users pane where you can select Suite Demo Team.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-manage-users.png)


    k. Select a test user, select **Edit**, and then select the **Access** tab.


    ![Screenshot shows the Manage Users pane where you can select Edit.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-edit-user.png)


    l. In the **Roles** pane, assign the appropriate role that you have created.


    ![Screenshot shows Administrator selected from Employee.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/netsuite-tutorial/ns-add-role.png)


    m. Select **Save**.

### Create the NetSuite test user

In this section, a user called B.Simon is created in NetSuite. NetSuite supports just-in-time user provisioning, which is enabled by default. There's no action item for you in this section. If a user doesn't already exist in NetSuite, a new one is created after authentication.

## Test SSO

In this section, you test your Microsoft Entra single sign-on configuration with following options.

- Select **Test this application**, and you should be automatically signed in to the NetSuite for which you set up the SSO
- You can use Microsoft My Apps. When you select the NetSuite tile in the My Apps, you should be automatically signed in to the NetSuite for which you set up the SSO. For more information about the My Apps, see [Introduction to the My Apps](https://support.microsoft.com/account-billing/sign-in-and-start-apps-from-the-my-apps-portal-2f3b1bae-0e5a-4a86-a33e-876fbd2a4510).

## Related content

Once you configure the NetSuite you can enforce session controls, which protects exfiltration and infiltration of your organization’s sensitive data in real time. Session controls extends from Conditional Access. [Learn how to enforce session control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/proxy-deployment-aad).
