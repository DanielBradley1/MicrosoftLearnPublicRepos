<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-hyperlink?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# hyperlink resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

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
