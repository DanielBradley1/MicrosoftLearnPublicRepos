<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connectivityconfigurationlink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# connectivityConfigurationLink resource type \(deprecated\)

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

Deprecated and to be retired soon. Use the [remoteNetworkConnectivityConfiguration resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetworkconnectivityconfiguration?view=graph-rest-beta) and its associated methods instead.

Specifies connectivity details for [deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) objects associated with a branch.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-branchconnectivityconfiguration-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.branchSite](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchconnectivityconfiguration?view=graph-rest-beta) | Retrieve the IPSec tunnel configuration required to establish a bidirectional communication link between your organization's router and the Microsoft gateway. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Specifies the name of the link. |
| id | String | A unique identifier for each link. |
| localConfigurations | [microsoft.graph.networkaccess.localConnectivityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-localconnectivityconfiguration?view=graph-rest-beta) collection | Specifies Microsoft's end of the tunnel configuration for a device link. |
| peerConfiguration | [microsoft.graph.networkaccess.peerConnectivityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-peerconnectivityconfiguration?view=graph-rest-beta) | Specifies the customer's end of the tunnel configuration for a device link. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.connectivityConfigurationLink",
  "id": "String (identifier)",
  "displayName": "String",
  "localConfigurations": [
    {
      "@odata.type": "microsoft.graph.networkaccess.localConnectivityConfiguration"
    }
  ],
  "peerConfiguration": {
    "@odata.type": "microsoft.graph.networkaccess.peerConnectivityConfiguration"
  }
}
```
