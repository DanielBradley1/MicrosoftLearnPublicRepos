<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# programControl resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

In the Microsoft Entra [access reviews](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta) feature, the program control object represents a control, linking an access review to a program.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create programControl](https://learn.microsoft.com/en-us/graph/api/programcontrol-create?view=graph-rest-beta) | [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) | Add a programControl to a program. |
| [Delete programControl](https://learn.microsoft.com/en-us/graph/api/programcontrol-delete?view=graph-rest-beta) | None. | Remove a programControl from a program. |
| [List programControls](https://learn.microsoft.com/en-us/graph/api/programcontrol-list?view=graph-rest-beta) | [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) collection | List controls across all programs in the tenant. |
| [List programControls of a program](https://learn.microsoft.com/en-us/graph/api/program-listcontrols?view=graph-rest-beta) | [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) collection | Get a collection of the controls of a program. |
| [List programControlTypes](https://learn.microsoft.com/en-us/graph/api/programcontroltype-list?view=graph-rest-beta) | [programControlType](https://learn.microsoft.com/en-us/graph/api/resources/programcontroltype?view=graph-rest-beta) collection | List program control types. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The feature-assigned identifier of the link between program and control. |
| programId | String | The programId of the program this control is a part of. Required on create. |
| controlId | String | The controlId of the control, in particular the identifier of an access review. Required on create. |
| controlTypeId | String | The programControlType identifies the type of program control - for example, a control linking to guest access reviews. Required on create. |
| displayName | String | The name of the control. |
| status | String | The life cycle status of the control. |
| createdDateTime | DateTimeOffset | The creation date and time of the program control. |
| owner | [userIdentity](https://learn.microsoft.com/en-us/graph/api/resources/useridentity?view=graph-rest-beta) | The user who created the program control. |
| resource | [programResource](https://learn.microsoft.com/en-us/graph/api/resources/programresource?view=graph-rest-beta) | The resource, a group or an app, targeted by this program control's access review. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| program | [program](https://learn.microsoft.com/en-us/graph/api/resources/program?view=graph-rest-beta) | The program this control is part of. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
 "id": "string (identifier)",
 "programId": "string (identifier)",
 "controlId": "string (identifier)",
 "controlTypeId": "string (identifier)",
 "displayName": "string",
 "status": "string",
 "createdDateTime": "string (timestamp)",
 "owner": {"@odata.type":"microsoft.graph.userIdentity"},
 "resource":{"@odata.type":"microsoft.graph.programResource"}
}
```
