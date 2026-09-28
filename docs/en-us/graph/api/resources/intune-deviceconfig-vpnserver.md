<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-vpnserver?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# vpnServer resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

VPN Server definition.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Description. |
| address | String | Address \(IP address, FQDN or URL\) |
| isDefaultServer | Boolean | Default server. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.vpnServer",
  "description": "String",
  "address": "String",
  "isDefaultServer": true
}
```
