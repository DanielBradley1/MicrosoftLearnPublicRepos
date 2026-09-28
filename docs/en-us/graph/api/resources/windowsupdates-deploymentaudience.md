<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# deploymentAudience resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The set of [updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) resources to which a [deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) can apply.

If the same **updatableAsset** resource is included in the **exclusions** and **members** relationships, deployment will not apply to it.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-list-deploymentaudiences?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) collection | Get a list of the [deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-post-deploymentaudiences?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) | Create a new [microsoft.graph.windowsUpdates.deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) | Read the properties and relationships of a [deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-delete?view=graph-rest-beta) | None | Delete a [deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta) object. |
| [List members](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-list-members?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) collection | List members of the [microsoft.graph.windowsUpdates.deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta). |
| [List exclusions](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-list-exclusions?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) collection | List exclusions of the [microsoft.graph.windowsUpdates.deploymentAudience](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentaudience?view=graph-rest-beta). |
| [Update members and exclusions](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-updateaudience?view=graph-rest-beta) | None | Add or remove members and exclusions. |
| [Update by ID](https://learn.microsoft.com/en-us/graph/api/windowsupdates-deploymentaudience-updateaudiencebyid?view=graph-rest-beta) | None | Add or remove members and exclusions of the same type. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for the deployment audience. Returned by default. Not nullable. Read-only. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| exclusions | [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) collection | Specifies the assets to exclude from the audience. |
| members | [microsoft.graph.windowsUpdates.updatableAsset](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatableasset?view=graph-rest-beta) collection | Specifies the assets to include in the audience. |
| applicableContent | [microsoft.graph.windowsUpdates.applicableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-applicablecontent?view=graph-rest-beta) collection | Content eligible to deploy to devices in the audience. Not nullable. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.deploymentAudience",
  "id": "String (identifier)"
}
```
