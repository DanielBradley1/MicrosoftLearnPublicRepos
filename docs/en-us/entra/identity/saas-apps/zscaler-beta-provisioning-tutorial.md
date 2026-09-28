<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/zscaler-beta-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Configure Zscaler Beta for automatic user provisioning with Microsoft Entra ID

The objective of this article is to demonstrate the steps to be performed in Zscaler Beta and Microsoft Entra ID to configure Microsoft Entra ID to automatically provision and de-provision users and/or groups to Zscaler Beta.

Note

This article describes a connector built on top of the Microsoft Entra user provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

Zscaler Beta is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| :---: | :---: | :---: |
| ✅ |  | ✅ |

## Prerequisites

The scenario outlined in this article assumes that you already have the following:

- A Microsoft Entra user account with an active subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- One of the following roles:

  - [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator)
  - [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator)
  - [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).

- A Zscaler Beta tenant
- A user account in Zscaler Beta with Admin permissions

Note

The Microsoft Entra provisioning integration relies on the Zscaler Beta SCIM API, which is available to Zscaler Beta developers for accounts with the Enterprise package.

## Step 1: Add Zscaler Beta from the gallery

Before configuring Zscaler Beta for automatic user provisioning with Microsoft Entra ID, you need to add Zscaler Beta from the Microsoft Entra application gallery to your list of managed SaaS applications.

**To add Zscaler Beta from the Microsoft Entra application gallery, perform the following steps:**

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **New application**.
3. In the search box, type **Zscaler Beta**, select **Zscaler Beta** from result panel then select **Add** button to add the application.

   ![Screenshot of Zscaler Beta in the results list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/search-new-app.png)

## Step 2: Assign users to Zscaler Beta

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user provisioning, only the users and/or groups that have been "assigned" to an application in Microsoft Entra ID are synchronized.

Before configuring and enabling automatic user provisioning, you should decide which users and/or groups in Microsoft Entra ID need access to Zscaler Beta. Once decided, you can assign these users and/or groups to Zscaler Beta by following the instructions here:

- [Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

### Important tips for assigning users to Zscaler Beta

- It's recommended that a single Microsoft Entra user is assigned to Zscaler Beta to test the automatic user provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to Zscaler Beta, you must select any valid application-specific role \(if available\) in the assignment dialog. Users with the **Default Access** role are excluded from provisioning.

## Step 3: Configure automatic user provisioning to Zscaler Beta

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in Zscaler Beta based on user and/or group assignments in Microsoft Entra ID.

Tip

You may also choose to enable SAML-based single sign-on for Zscaler Beta, following the instructions provided in the [Zscaler Beta single sign-on article](https://learn.microsoft.com/en-us/entra/identity/saas-apps/zscaler-beta-tutorial). Single sign-on can be configured independently of automatic user provisioning, though these two features complement each other.

Note

When users and groups are provisioned or de-provisioned we recommend to periodically restart provisioning to ensure that group memberships are properly updated. Doing a restart will force our service to re-evaluate all the groups and update the memberships.

### Configure automatic user provisioning for Zscaler Beta in Microsoft Entra ID

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **Zscaler Beta**.

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Zscaler Beta**.

   ![Screenshot that shows the Zscaler Beta link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot that shows the Provision tab of the Manage category is selected.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zscaler-beta-provisioning-tutorial/provisioning-tab.png)

5. Select **+ New configuration**.

   ![Screenshot of new configuration.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, enter the **Tenant URL** and **Secret Token** of your Zscaler Beta account as described later in this article.
7. To obtain the **Tenant URL** and **Secret Token**, navigate to **Administration > Authentication Settings** in the Zscaler Beta portal user interface and select **SAML** under **Authentication Type**.

   ![Screenshot that shows On Authentication Settings.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zscaler-beta-provisioning-tutorial/secret-token-1.png)


   Select **Configure SAML** to open the **Configuration SAML** options.


   ![Screenshot that shows On Configure SAML.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/zscaler-beta-provisioning-tutorial/secret-token-2.png)


   Select **Enable SCIM-Based Provisioning** to retrieve **Base URL** and **Bearer Token**, then save the settings. Copy the **Base URL** to **Tenant URL**, and **Bearer Token** to **Secret Token**.

8. Upon populating the fields shown in Step 5, select **Test Connection** to ensure Microsoft Entra ID can connect to Zscaler Beta. If the connection fails, ensure your Zscaler Beta account has Admin permissions and try again.

   ![Screenshot of Token.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-testconnection-tenanturltoken.png)

9. Select **Create** to create your configuration.
10. Select **Properties** on the **Overview** page.
11. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

12. Select **Attribute Mapping** in the left panel and select **users**.
13. Review the user attributes that are synchronized from Microsoft Entra ID to Zscaler Beta in the **Attribute Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Zscaler Beta for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Zscaler Beta |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | externalId | String |  | ✓ |
    | active | Boolean |  | ✓ |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
    | displayName | String |  | ✓ |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  | ✓ |
14. Select **Groups**.
15. Review the group attributes that are synchronized from Microsoft Entra ID to Zscaler Beta in the **Attribute Mappings** section. The attributes selected as **Matching** properties are used to match the groups in Zscaler Beta for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Zscaler Beta |
    | --- | --- | --- | --- |
    | displayName | String | ✓ | ✓ |
    | members | Reference |  |  |
    | externalId | String |  | ✓ |
16. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
17. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
18. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 4: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
