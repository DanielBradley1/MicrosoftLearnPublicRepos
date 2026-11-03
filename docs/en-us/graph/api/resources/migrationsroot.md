<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/migrationsroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-20 -->

# migrationsRoot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The root path from which migration actions are performed.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List crossTenantMigrationJobs](https://learn.microsoft.com/en-us/graph/api/migrationsroot-list-crosstenantmigrationjobs?view=graph-rest-beta) | [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) collection | List all of the crossTenantMigrationJobs for this tenant |
| [Create crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/migrationsroot-post-crosstenantmigrationjobs?view=graph-rest-beta) | [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) | Create a new crossTenantMigrationJob to migrate content to this tenant |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ID | String | migrations root ID. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| crossTenantMigrationJobs | [crossTenantMigrationJob](https://learn.microsoft.com/en-us/graph/api/resources/crosstenantmigrationjob?view=graph-rest-beta) collection | Migration Jobs associated with this tenant. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.migrationsRoot",
  "id": "String (identifier)"
}
```
