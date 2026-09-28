<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/adminwindowsupdates?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# adminWindowsUpdates resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an entity that acts as a container for all Windows Autopatch functionalities.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the device. Not nullable. Read-only. Returned by default. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| catalog | [microsoft.graph.windowsUpdates.catalog](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalog?view=graph-rest-beta) | Catalog of content that can be approved for deployment by Windows Autopatch. Read-only. |
| deploymentAudiences | [microsoft.graph.windowsUpdates.deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) collection | The set of [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) resources to which a [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) can apply. |
| deployments | [microsoft.graph.windowsUpdates.deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) collection | Deployments created using Windows Autopatch. |
| policies | [microsoft.graph.windowsUpdates.policy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-policy?view=graph-rest-beta) collection | A collection of policies for approving the deployment of different content to an audience over time. |
| products | [microsoft.graph.windowsUpdates.product](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-product?view=graph-rest-beta) collection | A collection of Windows products. |
| resourceConnections | [microsoft.graph.windowsUpdates.resourceConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-resourceconnection?view=graph-rest-beta) collection | Service connections to external resources such as analytics workspaces. |
| updatableAssets | [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) collection | Assets registered with Windows Autopatch that can receive updates. |
| updatePolicies | [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) collection | A collection of policies for approving the deployment of different content to an audience over time. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.adminWindowsUpdates",
  "id": "String (identifier)"
}
```
