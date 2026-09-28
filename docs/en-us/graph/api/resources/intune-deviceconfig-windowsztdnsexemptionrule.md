<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsexemptionrule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-09 -->

# windowsZtdnsExemptionRule resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Exemptions to ZTDNS rules for specific addresses or subnets

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description of the exemption rule |
| displayName | String | Name assigned to the exemption rule |
| ipAddresses | String collection | List of IPv4 and IPv6 addresses and subnets for this exemption rule. This collection can contain a maximum of 500 elements. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsZtdnsExemptionRule",
  "description": "String",
  "displayName": "String",
  "ipAddresses": [
    "String"
  ]
}
```
