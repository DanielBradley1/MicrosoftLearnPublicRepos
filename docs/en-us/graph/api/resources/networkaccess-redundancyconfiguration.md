<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-redundancyconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# redundancyConfiguration resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The redundancy option for a device link specifies the specific details and configuration settings related to redundancy.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| redundancyTier | microsoft.graph.networkaccess.redundancyTier | Specifies the Device link SKU .The possible values are: `noRedundancy`, `zoneRedundancy`. |
| zoneLocalIpAddress | String | Indicate the specific IP address used for establishing the Border Gateway Protocol \(BGP\) connection with Microsoft's network. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.redundancyConfiguration",
  "zoneLocalIpAddress": "String",
  "redundancyTier": "String"
}
```
