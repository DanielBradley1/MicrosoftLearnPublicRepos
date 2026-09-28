<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/unifiedstoragequota?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# unifiedStorageQuota resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides an aggregate view of a user's quota information across multiple services.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/unifiedstoragequota-get?view=graph-rest-beta) | [unifiedStorageQuota](https://learn.microsoft.com/en-us/graph/api/resources/unifiedstoragequota?view=graph-rest-beta) | Read the properties and relationships of a [unifiedStorageQuota](https://learn.microsoft.com/en-us/graph/api/resources/unifiedstoragequota?view=graph-rest-beta) object. |
| [List](https://learn.microsoft.com/en-us/graph/api/unifiedstoragequota-list-services?view=graph-rest-beta) | [serviceStorageQuotaBreakdown](https://learn.microsoft.com/en-us/graph/api/resources/servicestoragequotabreakdown?view=graph-rest-beta) collection | Get the list of services in a **serviceStorageQuotaBreakdown**. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The user ID. |
| manageWebUrl | String | A URL that can be used in a browser to manage the breakdown. Read-only. |
| remaining | Int64 | Total space remaining before reaching the quota limit in bytes. |
| state | usqState | Indicates the state of the storage space. The possible values are: `normal`, `nearing`, `critical`, `full`, and `overLimit`. |
| total | Int64 | Total allowed storage space in bytes. |
| used | Int64 | Total space used in bytes. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| services | [serviceStorageQuotaBreakdown](https://learn.microsoft.com/en-us/graph/api/resources/servicestoragequotabreakdown?view=graph-rest-beta) collection | The breakdown of services contributing to the user's quota usage. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.unifiedStorageQuota",
  "id": "String",
  "manageWebUrl": "String",
  "remaining": "Integer",
  "state": "normal | nearing | critical | full | overLimit",
  "total": "Integer",
  "used": "Integer"
}
```
