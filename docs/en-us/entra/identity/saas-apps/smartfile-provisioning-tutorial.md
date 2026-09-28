<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/smartfile-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Configure SmartFile for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in SmartFile and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to SmartFile.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

SmartFile is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ | ✅ |  |

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- \- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn). - One of the following roles: - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator) - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator) - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications)..
- [A SmartFile tenant](https://www.SmartFile.com/pricing/).
- A user account in SmartFile with Admin permissions.

## Assigning users to SmartFile

Microsoft Entra ID uses a concept called *assignments* to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to SmartFile. Once decided, you can assign these users and/or groups to SmartFile by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to SmartFile

- It's recommended that a single Microsoft Entra user is assigned to SmartFile to test the automatic user provisioning configuration. More users and/or groups may be assigned later.
- When assigning a user to SmartFile, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Set up SmartFile for provisioning

Before configuring SmartFile for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on SmartFile and collect more details needed.

1. Sign into your SmartFile Admin Console. Navigate to the top-right hand corner of the SmartFile Admin Console. Select **Product Key**.

   ![SmartFile Admin Console](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/smartfile-provisioning-tutorial/login.png)

2. To generate a bearer token, copy the **Product Key** and **Product Password**. Paste them in a notepad with a colon in between them.

   ![Screenshot of the Product Key section with the Product Key and Product Password text boxes called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/smartfile-provisioning-tutorial/auth.png)


   ![Screenshot of plaintext showing Product Key and Product Password separated by a colon.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/smartfile-provisioning-tutorial/key.png)

## Add SmartFile from the gallery

To configure SmartFile for automatic user provisioning with Microsoft Entra ID, you need to add SmartFile from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add SmartFile from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **SmartFile**, select **SmartFile** in the search box.
4. Select **SmartFile** from results panel and then add the app. Wait a few seconds while the app is added to your tenant. ![SmartFile in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configuring automatic user provisioning to SmartFile

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in SmartFile based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for SmartFile, following the instructions provided in the [SmartFile Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/smartfile-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other

### To configure automatic user provisioning for SmartFile in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **SmartFile**.

   ![Screenshot of the SmartFile link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your SmartFile Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to SmartFile. If the connection fails, ensure your SmartFile account has the required admin permissions and try again.

   Note

   Enter `https://<SmartFile sitename>.smartfile.com/ftp/scim` in the **Tenant URL**. Example : `https://demo1test.smartfile.com/ftp/scim`.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of the Provisioning properties page showing notification and deletion settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to SmartFile in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in SmartFile for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the SmartFile API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

    ![Screenshot of SmartFile user attribute mappings configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/smartfile-provisioning-tutorial/userattribute.png)

12. Review the group attributes that are synchronized from Microsoft Entra ID to SmartFile in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the groups in SmartFile for update operations. Select the **Save** button to commit any changes.

    ![Screenshot of SmartFile group attribute mappings configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/smartfile-provisioning-tutorial/groupattribute.png)

13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Connector limitations

- SmartFile only supports hard deletes.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

[Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
