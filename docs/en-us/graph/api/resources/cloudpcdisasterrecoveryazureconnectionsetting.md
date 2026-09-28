<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdisasterrecoveryazureconnectionsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-30 -->

# cloudPcDisasterRecoveryAzureConnectionSetting resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Azure network connection configuration of backup Cloud PCs provisioned for cross-region disaster recovery.

Inherits from [cloudPcDisasterRecoveryNetworkSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdisasterrecoverynetworksetting?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| onPremisesConnectionId | String | Indicates the unique ID of the virtual network that the new Cloud PC joins. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcDisasterRecoveryAzureConnectionSetting",
  "onPremisesConnectionId": "String"
}
```
