<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdisasterrecoverymicrosofthostednetworksetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-21 -->

# cloudPcDisasterRecoveryMicrosoftHostedNetworkSetting resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the configuration of Microsoft-hosted network for backup Cloud PCs provisioned for cross-region disaster recovery.

Inherits from [cloudPcDisasterRecoveryNetworkSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdisasterrecoverynetworksetting?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| regionGroup | [cloudPcRegionGroup](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcregiongroup?view=graph-rest-beta) | Indicates the logic geographic group this region belongs to. Multiple regions can belong to one region group. When a region group is configured for disaster recovery, the new Cloud PC is assigned to one of the regions within the group based on resource availability. For example, the `europeUnion` region group contains the North Europe and West Europe regions. |
| regionName | String | Indicates the Azure region that the new Cloud PC is assigned to. The Windows 365 service creates and manages the underlying virtual network. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcDisasterRecoveryMicrosoftHostedNetworkSetting",
  "regionGroup": "String",
  "regionName": "String"
}
```
