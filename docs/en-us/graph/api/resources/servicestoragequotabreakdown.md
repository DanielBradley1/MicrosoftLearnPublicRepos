<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/servicestoragequotabreakdown?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# serviceStorageQuotaBreakdown resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a proportion of the unified storage quota associated with a specific service.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/unifiedstoragequota-list-services?view=graph-rest-beta) | [serviceStorageQuotaBreakdown](https://learn.microsoft.com/en-us/graph/api/resources/servicestoragequotabreakdown?view=graph-rest-beta) collection | Get a list of services in the serviceStorageQuotaBreakdown. |
| [Get](https://learn.microsoft.com/en-us/graph/api/servicestoragequotabreakdown-get?view=graph-rest-beta) | [serviceStorageQuotaBreakdown](https://learn.microsoft.com/en-us/graph/api/resources/servicestoragequotabreakdown?view=graph-rest-beta) | Read the properties and relationships of a [serviceStorageQuotaBreakdown](https://learn.microsoft.com/en-us/graph/api/resources/servicestoragequotabreakdown?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The service breakdown name displayed to users. Localized. Read-only. |
| id | String | The service breakdown id. Read-only. |
| manageWebUrl | String | A URL that can be used in a browser to manage the service breakdown. Read-only. |
| used | Int64 | The number of bytes this service breakdown is consuming. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.serviceStorageQuotaBreakdown",
  "id": "String (identifier)",
  "displayName": "String",
  "manageWebUrl": "String",
  "used": "Integer"
}
```
