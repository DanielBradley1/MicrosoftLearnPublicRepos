<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/writebackconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# writebackConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a writeback state on Microsoft Entra cloud groups \(Microsoft 365 and security groups\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Indicates whether writeback of cloud groups to on-premise Active Directory is enabled. Default value is `true` for Microsoft 365 groups and `false` for security groups. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.writebackConfiguration",
  "isEnabled": "Boolean"
}
```
