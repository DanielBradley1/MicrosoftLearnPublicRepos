<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sharingoperationstatus?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-04 -->

# sharingOperationStatus resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the status of a particular sharing operation.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| disabledReason | String | Provides a description of why this operation is not enabled. Only returned if this operation is not enabled. |
| enabled | Boolean | Indicates whether this operation is enabled. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sharingOperationStatus",
  "enabled": "Boolean",
  "disabledReason": "String"
}
```
