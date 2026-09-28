<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtaskparameters?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# sharePointMigrationTaskParameters resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the parameters required to migrate a specific source resource in a source organization to a target organization, and other parameters that control the migration process. You must specify this resource when you create a new [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) using POST.

Base type of [sharePointGroupMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmigrationtaskparameters?view=graph-rest-beta), [sharePointSiteMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointsitemigrationtaskparameters?view=graph-rest-beta), and [sharePointUserMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointusermigrationtaskparameters?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| preferredLatestStartDateTime | DateTimeOffset | The preferred latest start date and time. The system cancels the **sharePointMigrationTask** if it doesn't start by this time. The value must be greater than the **preferredStartDateTime**, if present. Optional. Only on OneDrive and SharePoint. |
| preferredStartDateTime | DateTimeOffset | The preferred start date and time that allows the **sharePointMigrationTask** to start at a future time instead of as soon as possible \(default\). Optional. Only on OneDrive and SharePoint. |
| sourceSiteUrl | String | The SharePoint URL of the source site. Optional. Exactly one of **sourceSiteId** or **sourceUrl** must be specified. If both or neither are specified, it's an error. Only on OneDrive and SharePoint. |
| targetDataLocationCode | String | In Microsoft Entra, this value represents the geographic location \(for example, `JPN`, `NAM`\) of the target organization where the resource must be migrated to ensure data residency and compliance. This property isn't required for single-geo target organizations or when the migration is to the default GEO of a multi-geo target organization. Optional. Only on OneDrive and SharePoint. |
| targetOrganizationHost | String | The root, admin, or my site host of the specific multi-geo instance of the target organization where the resource must be migrated to ensure data residency and compliance. This property isn't required for single-geo target organizations or when the migration is to the default GEO of a multi-geo target organization. Optional. Only on OneDrive and SharePoint. |
| targetOrganizationId | Guid | The unique Microsoft Entra company ID of the target organization to which the source resource must be migrated. Only on OneDrive and SharePoint. |
| targetSiteUrl | String | The SharePoint URL of the target site. Only on OneDrive and SharePoint. |
| validateOnly | Boolean | Indicates whether this task is an actual migration or only a validation. If the parameter is missing, the system treats it as `false`. The default behavior is a real migration. Optional. Only on OneDrive and SharePoint. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharePointMigrationTaskParameters",
  "preferredLatestStartDateTime": "String (timestamp)",
  "preferredStartDateTime": "String (timestamp)",
  "sourceSiteUrl": "String",
  "targetDataLocationCode": "String",
  "targetOrganizationHost": "String",
  "targetOrganizationId": "Guid",
  "targetSiteUrl": "String",
  "validateOnly": "Boolean"
}
```
