<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/oneflow-provisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Configure Oneflow for automatic user provisioning with Microsoft Entra ID

This article describes the steps you need to perform in both Oneflow and Microsoft Entra ID to configure automatic user provisioning. When configured, Microsoft Entra ID automatically provisions and de-provisions users and groups to [Oneflow](https://oneflow.com) using the Microsoft Entra provisioning service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

## Supported capabilities

- Create users in Oneflow.
- Remove users in Oneflow when they don't require access anymore.
- Keep user attributes synchronized between Microsoft Entra ID and Oneflow.
- Provision groups and group memberships in Oneflow.
- [Single sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/oneflow-tutorial) to Oneflow \(recommended\).

## Prerequisites

The scenario outlined in this article assumes that you already have the following prerequisites:

- [A Microsoft Entra tenant](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-create-new-tenant).
- One of the following roles: [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator), [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator), or [Application Owner](https://learn.microsoft.com/en-us/entra/fundamentals/users-default-permissions#owned-enterprise-applications).
- A Oneflow tenant.
- A user account in Oneflow with Admin permissions.

## Step 1: Plan your provisioning deployment

1. Learn about [how the provisioning service works](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).
2. Determine who's in [scope for provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
3. Determine what data to [map between Microsoft Entra ID and Oneflow](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes).

## Step 2: Configure Oneflow to support provisioning with Microsoft Entra ID

Use the following information for [Step 5](#to-configure-automatic-user-provisioning-for-oneflow-in-microsoft-entra-id)-6.

- Tenant URL: `https://api.oneflow.com/scim/v1/`
- Secret Token: The oneflow SCIM token serves as the secret token in provisioning. Please follow the steps provided in this [article](https://developer.oneflow.com/docs/enable-scim-api-extension) for generating a Oneflow SCIM token.

## Step 3: Add Oneflow from the Microsoft Entra application gallery

Add Oneflow from the Microsoft Entra application gallery to start managing provisioning to Oneflow. If you have previously setup Oneflow for SSO you can use the same application. However it's recommended that you create a separate app when testing out the integration initially. Learn more about adding an application from the gallery [here](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal).

## Step 4: Define who is in scope for provisioning

The Microsoft Entra provisioning service allows you to scope who is provisioned based on assignment to the application, or based on attributes of the user or group. If you choose to scope who is provisioned to your app based on assignment, you can use the [steps to assign users and groups to the application](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal). If you choose to scope who is provisioned based solely on attributes of the user or group, you can [use a scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).

- Start small. Test with a small set of users and groups before rolling out to everyone. When scope for provisioning is set to assigned users and groups, you can control this by assigning one or two users or groups to the app. When scope is set to all users and groups, you can specify an [attribute based scoping filter](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
- If you need extra roles, you can [update the application manifest](https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps) to add new roles.

## Step 5: Configure automatic user provisioning to Oneflow

This section guides you through the steps to configure the Microsoft Entra provisioning service to create, update, and disable users and/or groups in TestApp based on user and/or group assignments in Microsoft Entra ID.

### To configure automatic user provisioning for Oneflow in Microsoft Entra ID:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**

   ![Screenshot of Enterprise applications blade.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/enterprise-applications.png)

3. In the applications list, select **Oneflow**.

   ![Screenshot of the Oneflow link in the Applications list.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/all-applications.png)

4. Select the **Provisioning** tab.

   ![Screenshot of Provisioning tab.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning.png)

5. Select **+ New configuration**.

   ![Screenshot of Provisioning tab automatic.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. In the **Tenant URL** field, enter your Oneflow Tenant URL and Secret Token. Select **Test Connection** to ensure Microsoft Entra ID can connect to Oneflow. If the connection fails, ensure your Oneflow account has the required admin permissions and try again.

   ![Screenshot of Provisioning test connection.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-test-connection.png)

7. Select **Create** to create your configuration.
8. Select **Properties** on the **Overview** page.
9. In the **Notification Email** field, enter the email address of a person who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

   ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

10. Select **Attribute Mapping** in the left panel and select **users**.
11. Review the user attributes that are synchronized from Microsoft Entra ID to Oneflow in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Oneflow for update operations. If you choose to change the [matching target attribute](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/customize-application-attributes), you need to ensure that the Oneflow API supports filtering users based on that attribute. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Oneflow |
    | --- | --- | --- | --- |
    | userName | String | ✓ | ✓ |
    | active | Boolean |  | ✓ |
    | externalId | String |  |  |
    | emails\[type eq "work"\].value | String |  |  |
    | name.givenName | String |  |  |
    | name.familyName | String |  |  |
    | phoneNumbers\[type eq "work"\].value | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:department | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:employeeNumber | String |  |  |
    | nickName | String |  |  |
    | title | String |  |  |
    | profileUrl | String |  |  |
    | displayName | String |  |  |
    | addresses\[type eq "work"\].streetAddress | String |  |  |
    | addresses\[type eq "work"\].locality | String |  |  |
    | addresses\[type eq "work"\].region | String |  |  |
    | addresses\[type eq "work"\].postalCode | String |  |  |
    | addresses\[type eq "work"\].country | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:costCenter | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:division | String |  |  |
    | urn:ietf:params:scim:schemas:extension:enterprise:2.0:User:organization | String |  |  |
    | urn:ietf:params:scim:schemas:extension:ws1b:2.0:User:adSourceAnchor | String |  |  |
    | urn:ietf:params:scim:schemas:extension:ws1b:2.0:User:customAttribute1 | String |  |  |
    | urn:ietf:params:scim:schemas:extension:ws1b:2.0:User:customAttribute2 | String |  |  |
    | urn:ietf:params:scim:schemas:extension:ws1b:2.0:User:customAttribute3 | String |  |  |
    | urn:ietf:params:scim:schemas:extension:ws1b:2.0:User:customAttribute4 | String |  |  |
    | urn:ietf:params:scim:schemas:extension:ws1b:2.0:User:customAttribute5 | String |  |  |
    | urn:ietf:params:scim:schemas:extension:ws1b:2.0:User:distinguishedName | String |  |  |
    | urn:ietf:params:scim:schemas:extension:ws1b:2.0:User:domain | String |  |  |
    | urn:ietf:params:scim:schemas:extension:ws1b:2.0:User:userPrincipalName | String |  |  |
12. Review the group attributes that are synchronized from Microsoft Entra ID to Oneflow in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the groups in Oneflow for update operations. Select the **Save** button to commit any changes.
    | Attribute | Type | Supported for filtering | Required by Oneflow |
    | --- | --- | --- | --- |
    | displayName | String | ✓ | ✓ |
    | externalId | String | ✓ | ✓ |
    | members | Reference |  |  |
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
