<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/tenantreference?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# tenantReference resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the information used to identify a Microsoft Entra tenant. This type is only used in the context of an [outboundSharedUserProfile](https://learn.microsoft.com/en-us/graph/api/resources/outboundshareduserprofile?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| tenantId | String | The identifier of the Microsoft Entra tenant. Read-only. Key. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.tenantReference",
  "tenantId": "String"
}
```
