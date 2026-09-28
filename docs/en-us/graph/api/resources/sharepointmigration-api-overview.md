<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigration-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-11-25 -->

# Use the SharePoint Embedded migration API

The SharePoint Embedded migration API enables developers to programmatically migrate large volumes of content from external sources \(for example, Azure blob storage\) into SharePoint Embedded containers. This API is designed for applications that require scalable, secure, and automated migration workflows.

## How to use the SharePoint Embedded migration API

The migration process involves four key steps using the following operations:

1. Provision SharePoint-managed Azure blob storage containers for temporary storage of file content and metadata.
2. Submit a migration job that copies content from the intermediary Azure blob storage containers into a specified SharePoint Embedded container.
3. Retrieve real-time status updates on the migration job, including success metrics and error logs.
4. Clean up pending migration jobs queued for processing.

## Common use cases

The Microsoft Graph API provides methods that support the common use cases for SharePoint Embedded migration.

| Use cases | REST resources |
| :--- | :--- |
| [Provision Azure blob storage containers](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-provisionmigrationcontainers?view=graph-rest-1.0) | [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) |
| [Create](https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-post-migrationjobs?view=graph-rest-1.0) and [delete](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationjob-delete?view=graph-rest-1.0) migration jobs | [sharePointMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationjob?view=graph-rest-1.0) |
| [Retrieve migration job progress](https://learn.microsoft.com/en-us/graph/api/sharepointmigrationjob-list-progressevents?view=graph-rest-1.0) | [sharePointMigrationEvent](https://learn.microsoft.com/en-us/graph/api/resources/sharepointmigrationevent?view=graph-rest-1.0) |

## Next steps

Use the Microsoft Graph API to migrate content into SharePoint Embedded containers. To learn more:

- Explore the resources and methods that are most helpful to your scenario.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
