<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmigrationtaskparameters?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# sharePointGroupMigrationTaskParameters resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the parameters necessary to migrate a specific group-connected site in a source organization to a target organization. You must specify this resource when you create a new [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) using POST.

Inherits from [sharePointMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| preferredLatestStartDateTime | DateTimeOffset | The preferred latest start date and time. The system cancels the **sharePointMigrationTask** if it doesn't start by this time. The value must be greater than the **preferredStartDateTime**, if present. Optional. Only on OneDrive and SharePoint. Inherited from [sharePointMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta). |
| preferredStartDateTime | DateTimeOffset | The preferred start date and time that allows the **sharePointMigrationTask** to start at a future time instead of as soon as possible \(default\). Optional. Only on OneDrive and SharePoint. Inherited from [sharePointMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta). |
| sourceGroupIdentity | [groupIdentity](https://learn.microsoft.com/en-us/graph/api/resources/groupidentity?view=graph-rest-beta) | The identity of the source group in the source tenant, including its mail nickname. |
| sourceSiteUrl | String | The SharePoint URL of the source site. Optional. Exactly one of **sourceSiteId** or **sourceUrl** must be specified. If both or neither are specified, it's an error. Only on OneDrive and SharePoint. Inherited from [sharePointMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta). |
| targetDataLocationCode | String | In Microsoft Entra, this value represents the geographic location \(for example, `JPN`, `NAM`\) of the target organization where the resource must be migrated to ensure data residency and compliance. This property isn't required for single-geo target organizations or when the migration is to the default GEO of a multi-geo target organization. Optional. Only on OneDrive and SharePoint. Inherited from [sharePointMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta). |
| targetGroupIdentity | [groupIdentity](https://learn.microsoft.com/en-us/graph/api/resources/groupidentity?view=graph-rest-beta) | The identity of the target group in the target tenant, including its mail nickname. |
| targetOrganizationHost | String | The root, admin, or my site host of the specific multi-geo instance of the target organization where the resource must be migrated to ensure data residency and compliance. This property isn't required for single-geo target organizations or when the migration is to the default GEO of a multi-geo target organization. Optional. Only on OneDrive and SharePoint. Inherited from [sharePointMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta). |
| targetOrganizationId | Guid | The unique Microsoft Entra company ID of the target organization to which the source resource must be migrated. Only on OneDrive and SharePoint. Inherited from [sharePointMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta). |
| targetSiteUrl | String | The SharePoint URL of the target site. Only on OneDrive and SharePoint. Inherited from [sharePointMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta). |
| validateOnly | Boolean | Indicates whether this task is an actual migration or only a validation. If the parameter is missing, the system treats it as `false`. The default behavior is a real migration. Optional. Only on OneDrive and SharePoint. Inherited from [sharePointMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointGroupMigrationTaskParameters",
  "targetOrganizationId": "Guid",
  "targetDataLocationCode": "String",
  "targetOrganizationHost": "String",
  "validateOnly": "Boolean",
  "preferredStartDateTime": "String (timestamp)",
  "preferredLatestStartDateTime": "String (timestamp)",
  "sourceSiteUrl": "String",
  "targetSiteUrl": "String",
  "sourceGroupIdentity": {
    "@odata.type": "microsoft.graph.groupIdentity"
  },
  "targetGroupIdentity": {
    "@odata.type": "microsoft.graph.groupIdentity"
  }
}
```
