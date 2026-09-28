<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionproxieddomaincollection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsInformationProtectionProxiedDomainCollection resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Information Protection Proxied Domain Collection

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name |
| proxiedDomains | [proxiedDomain](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-proxieddomain?view=graph-rest-1.0) collection | Collection of proxied domains |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionProxiedDomainCollection",
  "displayName": "String",
  "proxiedDomains": [
    {
      "@odata.type": "microsoft.graph.proxiedDomain",
      "ipAddressOrFQDN": "String",
      "proxy": "String"
    }
  ]
}
```
