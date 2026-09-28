<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/permissionsanalytics?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# permissionsAnalytics resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

Container for permissions analytics findings in Microsoft Entra Permissions Management.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| findings | [finding](https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta) collection | The output of the permissions usage data analysis performed by Permissions Management to assess risk with identities and resources. |
| permissionsCreepIndexDistributions | [permissionsCreepIndexDistribution](https://learn.microsoft.com/en-us/graph/api/resources/permissionscreepindexdistribution?view=graph-rest-beta) collection | Represents the Permissions Creep Index \(PCI\) for the authorization system. PCI distribution chart shows the classification of human and nonhuman identities based on the PCI score in three buckets \(low, medium, high\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.permissionsAnalytics",
  "id": "String (identifier)"
}
```
