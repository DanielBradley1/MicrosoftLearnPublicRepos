<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tunnelconfigurationikev2default?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# tunnelConfigurationIKEv2Default resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies connectivity settings such as protocol, IPSec policy, and preshared key\) for establishing connectivity.

Inherits from [microsoft.graph.networkaccess.tunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tunnelconfiguration?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| preSharedKey | String | A key to establish secure connection between the link and VPN tunnel on the edge. Inherited from [microsoft.graph.networkaccess.tunnelConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tunnelconfiguration?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tunnelConfigurationIKEv2Default",
  "preSharedKey": "String"
}
```
