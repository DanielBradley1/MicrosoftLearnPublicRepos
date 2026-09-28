<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tunnelconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# tunnelConfiguration resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies connectivity settings such as protocol, IPSec policy, and preshared key for a deviceLink, represented by a customer premises equipment \(CPE\), in a branchSite. This is an abstract type from which the [microsoft.graph.networkaccess.tunnelConfigurationIKEv2Custom](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tunnelconfigurationikev2custom?view=graph-rest-beta) and [microsoft.graph.networkaccess.tunnelConfigurationIKEv2Default](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tunnelconfigurationikev2default?view=graph-rest-beta) resource types are derived.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| preSharedKey | String | A key to establish secure connection between the link and VPN tunnel on the edge. |
| zoneRedundancyPreSharedKey | String | Another key for zone redundant tunnel. Required only when you select `zoneRedundancy` redindancyTier when creating a deviceLink. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tunnelConfiguration",
  "preSharedKey": "String",
  "zoneRedundancyPreSharedKey": "String"
}
```
