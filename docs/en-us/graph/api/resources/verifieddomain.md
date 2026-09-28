<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/verifieddomain?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# verifiedDomain resource type

Namespace: microsoft.graph

Specifies a domain for a tenant. The **verifiedDomains** property of the [organization](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0) entity is a collection of **verifiedDomain** objects.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| capabilities | String | For example, `Email`, `OfficeCommunicationsOnline`. |
| isDefault | Boolean | `true` if this is the default domain associated with the tenant; otherwise, `false`. |
| isInitial | Boolean | `true` if this is the initial domain associated with the tenant; otherwise, `false`. |
| name | String | The domain name; for example, `contoso.com`. |
| type | String | For example, `Managed`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "capabilities": "String",
  "isDefault": true,
  "isInitial": true,
  "name": "String",
  "type": "String"
}
```
