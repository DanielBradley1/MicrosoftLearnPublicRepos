<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/howspace-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-27 -->

# Configure Howspace for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Howspace and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and deprovisions users and groups to [Howspace](https://www.howspace.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Supported capabilities

- Create users in Howspace.
- Remove users in Howspace when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Howspace.
- Provision groups and group memberships in Howspace.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-setup-oidc-sso) to Howspace \(recommended\).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant)
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Howspace subscription with single sign-on and SCIM features enabled.
- A user account in Howspace with Main User Dashboard privileges.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Howspace](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Howspace to support provisioning with Microsoft Entra ID

### Single sign-on configuration

1. Sign in to the Howspace Main User Dashboard, then select **Settings** from the menu.
2. In the settings list, select **single sign-on**.

   ![Screenshot of the single sign-on section in the settings list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/howspace-provisioning-tutorial/settings-sso.png)

3. Select the **Add SSO configuration** button.

   ![Screenshot of the Add SSO configuration menu in the single sign-on section.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/howspace-provisioning-tutorial/settings-sso-2.png)

4. Select either **Microsoft Entra ID \(Multi-Tenant\)** or **Microsoft Entra ID** based on your organization's Microsoft Entra topology.

   ![Screenshot of the Microsoft Entra ID \(Multi-Tenant\) dialog.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/howspace-provisioning-tutorial/settings-azure-ad-multi-tenant.png) ![Screenshot of the Microsoft Entra dialog.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/howspace-provisioning-tutorial/settings-azure-ad-single-tenant.png)
5. Enter your Microsoft Entra tenant ID, and select **OK** to save the configuration.

### Provisioning configuration

1. In the settings list, select **System for Cross-domain Identity Management**.

   ![Screenshot of the System for Cross-domain Identity Management section in the settings list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/howspace-provisioning-tutorial/settings-scim.png)

2. Check the **Enable user synchronization** checkbox.
3. Copy the Tenant URL and Secret Token for later use in Microsoft Entra ID.
4. Select **Save** to save the configuration.

### Main user dashboard access control configuration

1. In the settings list, select **Main User Dashboard Access Control**

   ![Screenshot of the Main User Dashboard Access Control section in the settings list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/howspace-provisioning-tutorial/settings-access-control.png)

2. Check the **Enable single sign-on for main users** checkbox.
3. Select the SSO configuration you created in the previous step.
4. Enter the object IDs of the Microsoft Entra user groups that should have access to the Main User Dashboard to the **Limit to following user groups** field. You can specify multiple groups by separating the object IDs with a comma.
5. Select **Save** to save the configuration.

### Workspace default access control configuration

1. In the settings list, select **Workspace default settings**

   ![Screenshot of the Workspace default settings in the settings list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/howspace-provisioning-tutorial/settings-workspace-default.png)

2. In the Workspace default settings list, select **Login, registration and SSO**

   ![Screenshot of the Login, registration and SSO section in the Workspace default settings list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/howspace-provisioning-tutorial/settings-workspace-sso.png)

3. Check the **Users can login using single sign-on** checkbox.
4. Select the SSO configuration you created in the previous step.
5. Enter the object IDs of the Microsoft Entra user groups that should have access to workspaces to the **Limit to following user groups** field. You can specify multiple groups by separating the object IDs with a comma.
6. You can modify the user groups for each workspace individually after creating the workspace.

## Step 3: Add Howspace from the Microsoft Entra application gallery

Add Howspace from the Microsoft Entra application gallery to start managing provisioning to Howspace. If you have previously setup Howspace for SSO, you can use the same application. However it's recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Howspace

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Howspace in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Howspace**.

   ![Screenshot of the Howspace link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of the New configuration option on the Provisioning page.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Howspace Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Howspace. If the connection fails, ensure your Howspace account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.
10. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

    ![Screenshot of the Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

11. Select **Attribute Mapping** in the left panel and select **users**.
12. Review the user attributes that are synchronized from Microsoft Entra ID to Howspace in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Howspace for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Howspace API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Howspace |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | active | Boolean |  |  |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
    | phoneNumbers\[type eq "mobile"\].value | String |  |  |
    | externalId | String |  |  |
13. Under the **Mappings** section, select **Synchronize Microsoft Entra groups to Howspace**.
14. Review the group attributes that are synchronized from Microsoft Entra ID to Howspace in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Howspace for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Howspace |
    | --- | --- | --- | --- |
    | displayName | String | ✓ | ✓ |
    | externalId | String |  | ✓ |
    | members | Reference |  |  |
15. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
16. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
17. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

## Step 6: Monitor your deployment

Once you configure provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-provisioning-logs) to determine which users are provisioned successfully or unsuccessfully
2. Check the [progress bar](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user) to see the status of the provisioning cycle and how close it's to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application goes into quarantine. Learn more about quarantine states the [application provisioning quarantine status](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/application-provisioning-quarantine-status) article.

## More resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/configure-automatic-user-provisioning-portal)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)

## Related content

- [Learn how to review logs and get reports on provisioning activity](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning)
