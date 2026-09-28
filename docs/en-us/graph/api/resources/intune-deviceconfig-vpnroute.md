<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnroute?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# vpnRoute resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

VPN Route definition.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| destinationPrefix | String | Destination prefix \(IPv4/v6 address\). |
| prefixSize | Int32 | Prefix size. \(1-32\). Valid values 1 to 32 |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.vpnRoute",
  "destinationPrefix": "String",
  "prefixSize": 1024
}
```
