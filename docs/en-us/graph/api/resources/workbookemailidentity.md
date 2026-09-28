<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/workbookemailidentity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# workbookEmailIdentity resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an identity of an *actor*. For example, an actor can be a user who created, modified, or completed a task.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Display name of the user. |
| email | String | Email address of the user. |
| id | String | The unique identifier of the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.workbookEmailIdentity",
  "displayName": "String",
  "email": "String",
  "id": "String (identifier)"
}
```
