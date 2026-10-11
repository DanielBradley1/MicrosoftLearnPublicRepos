<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hyperlink?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-21 -->

# hyperlink resource type

Namespace: microsoft.graph.security

Note

The Microsoft Threat Intelligence APIs are available to all customers with a Microsoft Defender XDR or Microsoft Sentinel license. No separate license is required to access these APIs.

Represents the data used to create a hyperlink.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name for this **hyperlink**. |
| url | String | The URL for this **hyperlink**. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.hyperlink",
  "name": "String",
  "url": "String"
}
```
