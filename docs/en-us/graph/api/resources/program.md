<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/program?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-22 -->

# program resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

In the Microsoft Entra [access reviews](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta) feature, a program is a container, holding program controls. A tenant can have one or more programs. Each control links an access review to a program, to make it easier to locate related access reviews.

A tenant that has onboarded Microsoft Entra access reviews has one program, the `Default program`. An authorized administrator can create more programs, for example, to represent compliance initiatives.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create](https://learn.microsoft.com/en-us/graph/api/program-create?view=graph-rest-beta) | [program](https://learn.microsoft.com/en-us/graph/api/resources/program?view=graph-rest-beta) | Create a new program. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/program-delete?view=graph-rest-beta) | None. | Delete a program. |
| [List](https://learn.microsoft.com/en-us/graph/api/program-list?view=graph-rest-beta) | [program](https://learn.microsoft.com/en-us/graph/api/resources/program?view=graph-rest-beta) collection | Get a collection of all the programs. |
| [List controls](https://learn.microsoft.com/en-us/graph/api/program-listcontrols?view=graph-rest-beta) | [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) collection | Get a collection of the controls of a program. |
| [Update](https://learn.microsoft.com/en-us/graph/api/program-update?view=graph-rest-beta) | [program](https://learn.microsoft.com/en-us/graph/api/resources/program?view=graph-rest-beta) | Update a program. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The feature-assigned identifier of the program. |
| displayName | String | The name of the program. Required on create. |
| description | String | The description of the program. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| `controls` | [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) | Controls associated with the program. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
 "id": "string (identifier)",
 "displayName": "string",
 "description": "string"
}
```
