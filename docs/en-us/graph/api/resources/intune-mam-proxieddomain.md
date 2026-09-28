<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-proxieddomain?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# proxiedDomain resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Proxied Domain

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| ipAddressOrFQDN | String | The IP address or FQDN |
| proxy | String | Proxy IP or FQDN |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.proxiedDomain",
  "ipAddressOrFQDN": "String",
  "proxy": "String"
}
```
