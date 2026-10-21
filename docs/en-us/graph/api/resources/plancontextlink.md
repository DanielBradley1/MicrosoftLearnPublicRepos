<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# planContextLink resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A back-reference to where a [plan](https://learn.microsoft.com/en-us/graph/api/resources/plan?view=graph-rest-beta) is surfaced outside Planner \(for example, a Teams channel tab, a Loop page, or an Outlook calendar\). `webUrl`, `displayAs`, and `isActive` are returned by default.

Inherits from [plannerDelta](https://learn.microsoft.com/en-us/graph/api/resources/plannerdelta?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/plan-list-contexts?view=graph-rest-beta) | [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta) collection | Get a list of the planContextLink objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/plan-post-contexts?view=graph-rest-beta) | [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta) | Create a new planContextLink object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/plancontextlink-get?view=graph-rest-beta) | [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta) | Read the properties and relationships of [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/plancontextlink-update?view=graph-rest-beta) | [planContextLink](https://learn.microsoft.com/en-us/graph/api/resources/plancontextlink?view=graph-rest-beta) | Update the properties of a planContextLink object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/plan-delete-contexts?view=graph-rest-beta) | None | Delete a planContextLink object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| associationType | String | Describes how the plan is associated with the surface. |
| createdDateTime | DateTimeOffset | Date and time the context link was created. Read-only. |
| customLinkText | String | Custom text used to render the link, if provided. |
| displayAs | plannerPlanContextType | How the context link should be displayed. The possible values are: `teamsTab`, `sharePointPage`, `meetingNotes`, `other`, `unknownFutureValue`, `loopPage`, `project`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `loopPage` , `project`. |
| displayNameSegments | String collection | Display name segments used to render where the plan is surfaced. |
| id | String | The unique identifier of the entity. Read-only. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| isActive | Boolean | Indicates whether the context link is currently active. |
| isCreation | Boolean | Indicates whether this context link represents the original creation surface for the plan. |
| key | String | Identifier for the context the plan is surfaced in. |
| ownerAppId | String | Application ID of the app that owns the surface the plan is linked from. |
| webUrl | String | URL of the surface where the plan is displayed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.planContextLink",
  "id": "String (identifier)",
  "key": "String",
  "displayNameSegments": [
    "String"
  ],
  "webUrl": "String",
  "associationType": "String",
  "displayAs": "String",
  "isActive": "Boolean",
  "customLinkText": "String",
  "ownerAppId": "String",
  "isCreation": "Boolean",
  "createdDateTime": "String (timestamp)"
}
```
