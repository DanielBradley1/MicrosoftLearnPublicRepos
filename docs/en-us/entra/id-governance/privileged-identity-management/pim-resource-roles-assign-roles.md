<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-assign-roles -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Assign Azure resource roles in Privileged Identity Management

## Overview

With Microsoft Entra Privileged Identity Management \(PIM\), you can manage the built-in Azure resource roles, and custom roles, including \(but not limited to\):

- Owner
- User Access Administrator
- Contributor
- Security Admin
- Security Manager

Note

Users or members of a group assigned to the Owner or User Access Administrator subscription roles, and Microsoft Entra Global Administrators that enable subscription management in Microsoft Entra ID have Resource administrator permissions by default. These administrators can assign roles, configure role settings, and review access using Privileged Identity Management for Azure resources. A user can't manage Privileged Identity Management for Resources without Resource administrator permissions. View the list of [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles).

Privileged Identity Management supports both built-in and custom Azure roles. For more information on Azure custom roles, see [Azure custom roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/custom-roles).

Note

Agents and agent identities can receive and activate eligible Azure resource role assignments in preview. Each agent or agent identity requires an [E7 license](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals#privileged-identity-management).

## Role assignment conditions

Use Azure attribute-based access control \(Azure ABAC\) conditions to limit permissions in eligible Azure resource role assignments. Assignees must activate eligible assignments before they can use the permissions. PIM combines fine-grained resource conditions with time-bound assignments, approval workflows, and an audit trail.

Note

When a role is assigned, the assignment:

- Can't be assigned for a duration of less than five minutes
- Can't be removed within five minutes of it being assigned

Currently, the following built-in roles can have conditions added:

- [Storage Blob Data Contributor](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#storage-blob-data-contributor)
- [Storage Blob Data Owner](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#storage-blob-data-owner)
- [Storage Blob Data Reader](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles#storage-blob-data-reader)

For more information, see [What is Azure attribute-based access control \(Azure ABAC\)](https://learn.microsoft.com/en-us/azure/role-based-access-control/conditions-overview).

## Assign a role

Follow these steps to assign an Azure resource role to a user, group, agent, or agent identity.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a User Access Administrator.
2. Browse to **ID Governance** > **Privileged Identity Management** > **Azure resources**.
3. Select the **resource type** you want to manage. Start at either the **Management group** dropdown or the **Subscriptions** dropdown, and then further select **Resource groups** or **Resources** as needed. Select **Select** for the resource you want to manage to open its overview page.

   ![Screenshot that shows how to select Azure resources.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-list.png)
4. Under **Manage**, select **Roles** to see the list of roles for Azure resources.
5. Select **Add assignments** to open the **Add assignments** pane.

   ![Screenshot of Azure resources roles.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-roles.png)
6. Select a **Role** you want to assign.
7. Select the **No member selected** link to open the **Select a member or group** pane.

   ![Screenshot of the new assignment pane.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-select-role.png)
8. Select the user, group, agent, or agent identity you want to assign to the role and then choose **Select**.

   ![Screenshot that demonstrates how to select a member or group pane.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-select-member-or-group.png)
9. On the **Settings** tab, in the **Assignment type** list, select **Eligible** or **Active**.

   ![Screenshot of add assignments settings pane.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-membership-settings-type.png)

   Microsoft Entra PIM for Azure resources provides two distinct assignment types:

   - **Eligible** assignments require the member to activate the role before using it. Depending on the role settings, activation might require multifactor authentication \(MFA\), a business justification, or approval from designated approvers.
   - **Active** assignments don't require the member to activate the role before usage. Members assigned as active have the privileges assigned ready to use. This type of assignment is also available to customers who don't use Microsoft Entra PIM.

10. To specify a specific assignment duration, change the start and end dates and times.
11. If the role has been defined with actions that permit assignments to that role with conditions, then you can select **Add condition** to add a condition based on the principal user and resource attributes that are part of the assignment.

    ![Screenshot of the new assignment conditions pane.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/new-assignment-conditions.png)

    Conditions can be entered in the expression builder.

    ![Screenshot of the new assignment condition built from an expression.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/new-assignment-condition-expression.png)
12. When finished, select **Assign**.
13. After the new role assignment is created, a status notification is displayed.

    ![Screenshot of a new assignment notification.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-new-assignment-notification.png)

## Convert active role assignments to eligible role assignments \(Preview\)

Use the 'Assignments \(Preview\)' blade to change selected active Azure resource role assignments to eligible role assignments.

Enhanced Azure role assignment conversion is in preview. You can convert permanent active and time-bound active Azure resource role assignments to eligible role assignments.

Existing PIM licensing for Azure resources applies unchanged to users and groups. Eligible assignments for agents and agent identities require an E7 license. See [PIM licensing requirements](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals#privileged-identity-management).

The existing permissions for managing role assignments apply: you need the **Owner** or **User Access Administrator** role at the scope you want to manage.

When the role assignment conversion takes effect, the eligible role assignment replaces the active role assignment. The user must activate the eligible role assignment. The eligible role assignment's **Start time** and **End time** define when the user can request activation, not the duration of each role activation. Role activation duration follows the [role's activation settings](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-configure-role-settings#activation-maximum-duration).

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Open **Privileged Identity Management**, select **Azure resources**, and select the Azure scope you want to manage.
3. Select **Assignments \(Preview\)**, and then select **Active Assignments**.
4. Select the role assignments you want to change, and then select **Manage Assignments**.

   [![Screenshot of Active Assignments with a role assignment selected and the Manage Assignments action available.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/active-assignment-manage.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/active-assignment-manage.png#lightbox)
5. In **Update Assignments**, under **Target Assignment Type**, select **Eligible \(Recommended\)**.
6. Under **Assignment duration**, select **Time-bound**, and specify **Start time** and **End time**.

   [![Screenshot of Update Assignments with Eligible and Time-bound selected and the eligibility start and end times shown.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/update-assignment-to-eligible.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/update-assignment-to-eligible.png#lightbox)
7. Select **Save**.
8. Review **Eligible Assignments** to check the role assignment type and duration.

After setup, users can [activate their eligible Azure resource role assignments in My Access](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-activate-your-roles?pivots=my-access#activate-an-azure-resource-role-in-my-access).

## Assign a role using Azure Resource Manager API

Privileged Identity Management supports Azure Resource Manager \(ARM\) API commands to manage Azure resource roles, as documented in the [PIM Azure Resource Manager API reference](https://learn.microsoft.com/en-us/rest/api/authorization/role-eligibility-schedule-requests). For the permissions required to use the PIM API, see [Understand the Privileged Identity Management APIs](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-apis).

The following example is a sample HTTP request to create an eligible assignment for an Azure role.

### Request

```HTTP
PUT https://management.azure.com/providers/Microsoft.Subscription/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/providers/Microsoft.Authorization/roleEligibilityScheduleRequests/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e?api-version=2020-10-01-preview
```

### Request body

```JSON
{
  "properties": {
    "principalId": "aaaaaaaa-bbbb-cccc-1111-222222222222",
    "roleDefinitionId": "/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/providers/Microsoft.Authorization/roleDefinitions/c8d4ff99-41c3-41a8-9f60-21dfdad59608",
    "requestType": "AdminAssign",
    "scheduleInfo": {
      "startDateTime": "2022-07-05T21:00:00.91Z",
      "expiration": {
        "type": "AfterDuration",
        "endDateTime": null,
        "duration": "P365D"
      }
    },
    "condition": "@Resource[Microsoft.Storage/storageAccounts/blobServices/containers:ContainerName] StringEqualsIgnoreCase 'foo_storage_container'",
    "conditionVersion": "1.0"
  }
}
```

Note

The `duration` field \(value `P365D` in this example\) sets the eligible assignment to expire after 365 days. To create permanent eligibility, configure the role management policy at the target scope to allow it.

### Response

Status code: 201

```HTTP
{
  "properties": {
    "targetRoleEligibilityScheduleId": "b1477448-2cc6-4ceb-93b4-54a202a89413",
    "targetRoleEligibilityScheduleInstanceId": null,
    "scope": "/providers/Microsoft.Subscription/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e",
    "roleDefinitionId": "/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/providers/Microsoft.Authorization/roleDefinitions/c8d4ff99-41c3-41a8-9f60-21dfdad59608",
    "principalId": "aaaaaaaa-bbbb-cccc-1111-222222222222",
    "principalType": "User",
    "requestType": "AdminAssign",
    "status": "Provisioned",
    "approvalId": null,
    "scheduleInfo": {
      "startDateTime": "2022-07-05T21:00:00.91Z",
      "expiration": {
        "type": "AfterDuration",
        "endDateTime": null,
        "duration": "P365D"
      }
    },
    "ticketInfo": {
      "ticketNumber": null,
      "ticketSystem": null
    },
    "justification": null,
    "requestorId": "a3bb8764-cb92-4276-9d2a-ca1e895e55ea",
    "createdOn": "2022-07-05T21:00:45.91Z",
    "condition": "@Resource[Microsoft.Storage/storageAccounts/blobServices/containers:ContainerName] StringEqualsIgnoreCase 'foo_storage_container'",
    "conditionVersion": "1.0",
    "expandedProperties": {
      "scope": {
        "id": "/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e",
        "displayName": "Pay-As-You-Go",
        "type": "subscription"
      },
      "roleDefinition": {
        "id": "/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/providers/Microsoft.Authorization/roleDefinitions/c8d4ff99-41c3-41a8-9f60-21dfdad59608",
        "displayName": "Contributor",
        "type": "BuiltInRole"
      },
      "principal": {
        "id": "a3bb8764-cb92-4276-9d2a-ca1e895e55ea",
        "displayName": "User Account",
        "email": "user@my-tenant.com",
        "type": "User"
      }
    }
  },
  "name": "64caffb6-55c0-4deb-a585-68e948ea1ad6",
  "id": "/providers/Microsoft.Subscription/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/providers/Microsoft.Authorization/RoleEligibilityScheduleRequests64caffb6-55c0-4deb-a585-68e948ea1ad6",
  "type": "Microsoft.Authorization/RoleEligibilityScheduleRequests"
}
```

## Update or remove an existing role assignment

Follow these steps to update or remove an existing role assignment.

1. Open **Microsoft Entra Privileged Identity Management**.
2. Select **Azure resources**.
3. Select the **resource type** you want to manage. Start at either the **Management group** dropdown or the **Subscriptions** dropdown, and then further select **Resource groups** or **Resources** as needed. Select **Select** for the resource you want to manage to open its overview page.

   ![Screenshot that shows how to select Azure resources to update.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-list.png)
4. Under **Manage**, select **Roles** to list the roles for Azure resources. The following screenshot lists the roles of an Azure Storage account. Select the role that you want to update or remove.

   ![Screenshot that shows the roles of an Azure Storage account.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-update-select-role.png)
5. Find the role assignment on the **Eligible roles** or **Active roles** tabs.

   [![Screenshot demonstrates how to update or remove role assignment.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-update-remove.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-update-remove.png#lightbox)
6. To add or update a condition to refine Azure resource access, select **Add** or **View/Edit** in the **Condition** column for the role assignment.
7. Select **Add expression** or **Delete** to update the expression. You can also select **Add condition** to add a new condition to your role.

   [![Screenshot that demonstrates how to update or remove attributes of a role assignment.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-abac-update-remove.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-assign-roles/resources-abac-update-remove.png#lightbox)

   For information about extending a role assignment, see [Extend or renew Azure resource roles in Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-renew-extend).

## Next steps

- [Configure Azure resource role settings in Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-configure-role-settings)
- [Assign Microsoft Entra roles in Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-how-to-add-role-to-user)
