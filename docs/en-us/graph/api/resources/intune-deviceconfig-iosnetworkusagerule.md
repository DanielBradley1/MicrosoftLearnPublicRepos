<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iosnetworkusagerule?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosNetworkUsageRule resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Network Usage Rules allow enterprises to specify how managed apps use networks, such as cellular data networks.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| managedApps | [appListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applistitem?view=graph-rest-1.0) collection | Information about the managed apps that this rule is going to apply to. This collection can contain a maximum of 500 elements. |
| cellularDataBlockWhenRoaming | Boolean | If set to true, corresponding managed apps will not be allowed to use cellular data when roaming. |
| cellularDataBlocked | Boolean | If set to true, corresponding managed apps will not be allowed to use cellular data at any time. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosNetworkUsageRule",
  "managedApps": [
    {
      "@odata.type": "microsoft.graph.appListItem",
      "name": "String",
      "publisher": "String",
      "appStoreUrl": "String",
      "appId": "String"
    }
  ],
  "cellularDataBlockWhenRoaming": true,
  "cellularDataBlocked": true
}
```
