<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationsroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# sharePointMigrationsRoot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the root container for SharePoint resources and services in Microsoft Graph. This resource provides access to SharePoint migration operations and user and group identity mappings used during migration processes.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get SharePoint group identity mapping](https://learn.microsoft.com/en-us/graph/api/sharepointgroupidentitymapping-get?view=graph-rest-beta) | [sharePointGroupIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta) | Retrieves a specific cross-organization group identity mapping based on the source group's Azure AD object ID. |
| [Update SharePoint group identity mapping](https://learn.microsoft.com/en-us/graph/api/sharepointgroupidentitymapping-update?view=graph-rest-beta) | [sharePointGroupIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta) collection | Performs delta patch operations on group identity mappings for cross-organization migration. |
| [Get SharePoint user identity mapping](https://learn.microsoft.com/en-us/graph/api/sharepointuseridentitymapping-get?view=graph-rest-beta) | [sharePointUserIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta) | Retrieves a specific user identity mapping by source user principal name \(UPN\). |
| [Update SharePoint user identity mapping](https://learn.microsoft.com/en-us/graph/api/sharepointuseridentitymapping-update?view=graph-rest-beta) | [sharePointUserIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta) collection | Performs delta patch operations on user identity mappings for cross-organization migration. |
| SharePoint migration task |  |  |
| [Get](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-get?view=graph-rest-beta) | [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) | Get a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) that was previously created, using the task ID. |
| [Create or update](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-update?view=graph-rest-beta) | [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) | Create or update a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) to migrate a resource from the source organization to the target organization, using the **sharePointMigrationTaskParameters**. |
| [Get by source user principal name](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-getbysourceuserprincipalname?view=graph-rest-beta) | [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) | Get a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) that was previously created for a user, using the source **userPrincipalName**. |
| [Get by source site URL](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-getbysourcesiteurl?view=graph-rest-beta) | [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) | Get a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) that was previously created for a regular site, using the source site URL. |
| [Get by source group mail nickname](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-getbysourcegroupmailnickname?view=graph-rest-beta) | [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) | Get a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) that was previously created for a group, using the source group mail nickname. |
| [Cancel](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationtask-cancel?view=graph-rest-beta) | None | Cancel a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) that moves a specific object from a source organization to a target organization. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the **sharePointMigrationsRoot** resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| crossOrganizationGroupMappings | [sharePointGroupIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta) collection | Collection of group identity mappings for cross-organization migration. |
| crossOrganizationMigrationTasks | [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) collection | A collection of **sharePointMigrationTask** resources that represent cross-organization migration tasks. |
| crossOrganizationUserMappings | [sharePointUserIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta) collection | Collection of user identity mappings for cross-organization migration. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationsRoot",
  "id": "String (identifier)"
}
```
