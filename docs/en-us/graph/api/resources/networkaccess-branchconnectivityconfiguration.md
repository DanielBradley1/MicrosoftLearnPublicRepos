<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchconnectivityconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# branchConnectivityConfiguration resource type \(deprecated\)

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Specifies the connectivity details of all device links associated with a branch.

Important

Deprecated and to be retired soon. Use the [remoteNetworkConnectivityConfiguration resource type](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-remotenetworkconnectivityconfiguration?view=graph-rest-beta) and its associated methods instead.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-branchconnectivityconfiguration-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.branchConnectivityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchconnectivityconfiguration?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.networkaccess.branchConnectivityConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-branchconnectivityconfiguration?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| branchId | String | Unique identifier or a specific reference assigned to a branchSite. Key. |
| branchName | String | Display name assigned to a branchSite. |
| links | [microsoft.graph.networkaccess.connectivityConfigurationLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connectivityconfigurationlink?view=graph-rest-beta) collection | List of connectivity configurations for [deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) objects. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| links | [microsoft.graph.networkaccess.connectivityConfigurationLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-connectivityconfigurationlink?view=graph-rest-beta) collection | List of connectivity configurations for [deviceLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-devicelink?view=graph-rest-beta) objects. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.branchConnectivityConfiguration",
  "branchId": "String (identifier)",
  "branchName": "String"
}
```
