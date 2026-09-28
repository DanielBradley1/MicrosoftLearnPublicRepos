<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepoint-crossorganization-api-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Use the SharePoint cross-tenant migration API \(preview\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The SharePoint cross-tenant migration APIs enable organizations to manage the tasks and identity mappings during tenant-to-tenant migrations. These APIs are used to migrate a specific source resource in a source organization to a target organization.

## How to use the SharePoint migration task API

The migration process involves three key steps using the following operations:

1. Create a [sharePointMigrationTask](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationtask?view=graph-rest-beta) to migrate a resource from the source organization to the target organization.
2. Get the **sharePointMigrationTask** that was previously created, using the ID, **sourceUserPrincipalName**, **sourceSiteUrl**, or **sourceGroupObjectId** of the task.
3. Cancel the migration task queued for processing.

## Common use cases

The Microsoft Graph API provides methods that support the common use cases for SharePoint cross-tenant migration.

| Use cases | REST resources |
| :--- | :--- |
| Migrate a specific *user* in a source tenant to a target tenant | [sharePointUserMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointusermigrationtaskparameters?view=graph-rest-beta) |
| Migrate a specific *regular site* in a source tenant to a target tenant | [sharePointSiteMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointsitemigrationtaskparameters?view=graph-rest-beta) |
| Migrate a specific *group-connected site* in a source tenant to a target tenant | [sharePointGroupMigrationTaskParameters](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupmigrationtaskparameters?view=graph-rest-beta) |
| Retrieve a specific group identity mapping and perform delta operations on group identity mappings | [sharePointGroupIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointgroupidentitymapping?view=graph-rest-beta) |
| Retrieve a specific user identity mapping and perform delta operations on user identity mappings | [sharePointUserIdentityMapping](https://learn.microsoft.com/en-us/graph/api/resources/sharepointuseridentitymapping?view=graph-rest-beta) |

## Next steps

Use the Microsoft Graph API to manage the tasks and identity mappings during tenant-to-tenant migrations. To learn more:

- Explore the resources and methods that are most helpful to your scenario.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
