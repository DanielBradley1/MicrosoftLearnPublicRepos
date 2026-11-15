<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resourcequota?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-10 -->

# resourceQuota resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a quota configuration for a resource type in a Microsoft Entra organization. Configure this object through the **resourceQuotas** property of an [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-beta) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| maxPercentage | Int32 | The maximum percentage of the organization's `directorySizeQuota.total` that this resource type can consume. The value must be between `0` and `100`. A value of `0` blocks creation of new resources of this type. If omitted for supported resource types, the default is `80`. |
| resourceType | [resourceQuotaType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#resourcequotatype-values) | The resource type to which the quota applies. Each value must be unique within the organization's **resourceQuotas** collection. The possible values are: `agentIdentityBlueprint`, `agentIdentity`, `managedIdentity`, `unknownFutureValue`. |
| total | Int32 | The effective maximum number of resources allowed, calculated from `directorySizeQuota.total` and **maxPercentage**. This value is read-only and changes when the organization's overall quota changes. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.resourceQuota",
  "resourceType": "String",
  "maxPercentage": "Int32",
  "total": "Int32"
}
```
