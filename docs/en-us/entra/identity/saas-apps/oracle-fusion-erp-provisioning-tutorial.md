<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/oracle-fusion-erp-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Configure Oracle Fusion ERP for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Oracle Fusion ERP and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Oracle Fusion ERP.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- 

  - A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
  - One of the following roles:

    - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
    - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
    - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- An [Oracle Fusion ERP tenant](https://www.oracle.com/applications/erp/).
- A user account in Oracle Fusion ERP with Admin permissions.

## Assign Users to Oracle Fusion ERP

Microsoft Entra ID uses a concept called assignments to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been assigned to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Oracle Fusion ERP. Once decided, you can assign these users and/or groups to Oracle Fusion ERP by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Important tips for assigning users to Oracle Fusion ERP

- It's recommended that a single Microsoft Entra user is assigned to Oracle Fusion ERP to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Oracle Fusion ERP, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the Default Access role are excluded from provisioning.

## Set up Oracle Fusion ERP for provisioning

Before configuring Oracle Fusion ERP for automatic user provisioning with Microsoft Entra ID, you need to enable SCIM provisioning on Oracle Fusion ERP.

1. Sign in to your [Oracle Fusion ERP Admin Console](https://cloud.oracle.com/sign-in)
2. Select the Navigator on the top-left top corner. Under **Tools**, select **Security Console**.

   ![Screenshot of the Navigator page in the Oracle Fusion E R P admin console. Tools and Security console are highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/oracle-fusion-erp-provisioning-tutorial/login.png)

3. Navigate to **Users**.

   ![Screenshot of a panel in the Oracle Fusion E R P admin console. The Users item is highlighted.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/oracle-fusion-erp-provisioning-tutorial/user.png)

4. Save the username and password for the admin user account which you use to log into the Oracle Fusion ERP admin console. These values need to be entered in the **Admin Username** and **Password** fields in the Provisioning tab of your Oracle Fusion ERP application.

## Add Oracle Fusion ERP from the gallery

To configure Oracle Fusion ERP for automatic user provisioning with Microsoft Entra ID, you need to add Oracle Fusion ERP from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Oracle Fusion ERP from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the **Add from the gallery** section, type **Oracle Fusion ERP**, select **Oracle Fusion ERP** in the results panel.

   ![Oracle Fusion ERP in the results list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Configure automatic user provisioning to Oracle Fusion ERP

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Oracle Fusion ERP based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Oracle Fusion ERP by following the instructions provided in the [Oracle Fusion ERP Single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/oracle-fusion-erp-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other.

Note

To learn more about Oracle Fusion ERP's SCIM endpoint, refer to [REST API for Common Features in Oracle Applications Cloud](https://docs.oracle.com/en/cloud/saas/applications-common/23b/farca/index.html).

### To configure automatic user provisioning for Fuze in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Oracle Fusion ERP**.

   ![The Oracle Fusion ERP link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of the Manage options with the Provisioning option called out.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Oracle Fusion ERP Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Oracle Fusion ERP. If the connection fails, ensure your Oracle Fusion ERP account has the required admin permissions and try again.

   Note

   Enter `https://ejlv.fa.em2.oraclecloud.com/hcmRestApi/scim/` in the **Tenant URL**.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)


   ![Screenshot of the Admin credentials section. A Test connection button and fields for a Tenant U R L, admin username, and admin password are visible.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/oracle-fusion-erp-provisioning-tutorial/admin.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of the Provisioning properties page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Oracle Fusion ERP in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Oracle Fusion ERP for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Oracle Fusion ERP API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Oracle Fusion ERP |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | externalId | String |  |  |
    | displayName | String |  |  |
    | preferredLanguage | String |  |  |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
    | emails\[type eq "work"\].value | String |  |  |
    | active | Boolean |  |  |
12. Review the group attributes that are synchronized from Microsoft Entra ID to Oracle Fusion ERP in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Oracle Fusion ERP for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Oracle Fusion ERP |
    | --- | --- | --- | --- |
    | displayName | String | ✓ | ✓ |
    | members | Reference |  |  |
13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Connector limitations

- Oracle Fusion ERP only supports Basic Authentication for their SCIM endpoint.
- Oracle Fusion ERP doesn't support group provisioning.
- Roles in Oracle Fusion ERP are mapped to groups in Microsoft Entra ID. To assign roles to users in Oracle Fusion ERP from Microsoft Entra ID, you need to assign users to the desired Microsoft Entra groups that are named after roles in Oracle Fusion ERP.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
