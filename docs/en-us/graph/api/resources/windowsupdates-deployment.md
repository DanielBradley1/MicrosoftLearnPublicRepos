<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# deployment resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the deployment of content to a set of devices.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List deployments](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-list-deployments?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) collection | Get a list of the [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) objects and their properties. |
| [Create deployment](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-post-deployments?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) | Create a new [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) object. |
| [Get deployment](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deployment-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) | Read the properties and relationships of a [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) object. |
| [Update deployment](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deployment-update?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) | Update the properties of a [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) object. |
| [Delete deployment](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deployment-delete?view=graph-rest-beta) | None | Deletes a [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) object. |
| [List members](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-list-members?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) collection | List members of the deployment audience. |
| [List exclusions](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-list-exclusions?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) collection | List exclusions from the deployment audience. |
| [Update members and exclusions](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-updateaudience?view=graph-rest-beta) | None | Add or remove members and exclusions of the deployment audience. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | [microsoft.graph.windowsUpdates.deployableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployablecontent?view=graph-rest-beta) | Specifies what content to deploy. Cannot be changed. Returned by default. |
| createdDateTime | DateTimeOffset | The date and time the deployment was created. Returned by default. Read-only. |
| id | String | The unique identifier for the deployment. Returned by default. Key. Not nullable. Read-only. |
| lastModifiedDateTime | DateTimeOffset | The date and time the deployment was last modified. Returned by default. Read-only. |
| settings | [microsoft.graph.windowsUpdates.deploymentSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentsettings?view=graph-rest-beta) | Settings specified on the specific deployment governing how to deploy **content**. Returned by default. |
| state | [microsoft.graph.windowsUpdates.deploymentState](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentstate?view=graph-rest-beta) | Execution status of the deployment. Returned by default. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| audience | [microsoft.graph.windowsUpdates.deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) | Specifies the audience to which content is deployed. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.deployment",
  "id": "String (identifier)",
  "state": {
    "@odata.type": "microsoft.graph.windowsUpdates.deploymentState"
  },
  "content": {
    "@odata.type": "microsoft.graph.windowsUpdates.deployableContent"
  },
  "settings": {
    "@odata.type": "microsoft.graph.windowsUpdates.deploymentSettings"
  },
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)"
}
```
