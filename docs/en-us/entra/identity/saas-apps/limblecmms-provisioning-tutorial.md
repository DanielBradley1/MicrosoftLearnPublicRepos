<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/limblecmms-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Configure LimbleCMMS for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both LimbleCMMS and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [LimbleCMMS](https://limblecmms.com/) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Capabilities Supported

- Create users in LimbleCMMS.
- Remove users in LimbleCMMS when they don't require access anymore.
- Creates groups in LimbleCMMS.
- Adds/Removes users from groups in LimbleCMMS
- Removes groups in LimbleCMMS
- Keep user attributes synchronized between Microsoft Entra ID and LimbleCMMS.
- Provision groups and group memberships in LimbleCMMS.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-setup-oidc-sso) to LimbleCMMS \(recommended\).
- Long lived bearer token authentication supported.

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A [LimbleCMMS](https://limblecmms.com/signup/?plan=business-yearly) tenant with Business Plus or above licensing.
- A user account in LimbleCMMS with Super Admin permissions.
- Single Sign On to be enabled in your LimbleCMMS tenant \(contact your Customer Success Manager\).
- At least one group you plan on provisioning to LimbleCMMS \(permissions in LimbleCMMS are based on groups, if you don't provision a group then the users that are provisioned don't have any permissions associated with them\).

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and LimbleCMMS](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure LimbleCMMS to support provisioning with Microsoft Entra ID

1. Login to LimbleCMMS as a **Super Admin**.
2. Navigate to **Advanced Settings > Manage SSO**. ![Manage SSO](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/limblecmms-provisioning-tutorial/limble-manage-sso.png)
3. Select **Microsoft Entra ID** as your SSO Provider.
4. [Setup OIDC](https://help.limblecmms.com/en/articles/4446986-active-directory-oidc-sso-setup-guide) to support Single Sign On
5. Select the **Generate SCIM Token** button to retrieve your SCIM token, save this for a future step.
6. Select **"Enable SSO"**.

## Step 3: Add LimbleCMMS from the Microsoft Entra application gallery

Add LimbleCMMS from the Microsoft Entra application gallery to start managing provisioning to LimbleCMMS. If you have previously setup LimbleCMMS for SSO you can use the same application. However, we recommend that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to LimbleCMMS

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in LimbleCMMS based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for LimbleCMMS in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Enterprise applications blade](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **LimbleCMMS**.

   ![The LimbleCMMS link in the Applications list](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Provisioning tab](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your LimbleCMMS Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to LimbleCMMS. If the connection fails, ensure your LimbleCMMS account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to LimbleCMMS in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in LimbleCMMS for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the LimbleCMMS API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | userName | String | ✓ |
    | active | Boolean |  |
    | emails\[type eq "work"\].value | String |  |
    | name.givenName | String |  |
    | name.familyName | String |  |
    | externalId | String |  |
12. Review the group attributes that are synchronized from Microsoft Entra ID to LimbleCMMS in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in LimbleCMMS for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering |
    | --- | --- | --- |
    | displayName | String | ✓ |
    | members | Reference |  |
    | externalId | String |  |
13. To configure scoping filters, refer to the instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
14. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
15. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

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
