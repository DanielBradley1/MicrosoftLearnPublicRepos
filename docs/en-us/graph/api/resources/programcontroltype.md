<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/programcontroltype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-21 -->

# programControlType resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

In the Microsoft Entra [access reviews](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta) feature, the program control type is used when associating a control to a program, to indicate the type of access review the control is for.

The program control type objects are automatically generated when an authorized administrator onboards the tenant to use the access reviews feature. No additional program control types can be created.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/programcontroltype-list?view=graph-rest-beta) | [programControlType](https://learn.microsoft.com/en-us/graph/api/resources/programcontroltype?view=graph-rest-beta) collection | List program control types. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The feature-assigned identifier of the program control type |
| displayName | String | The name of the program control type |

## Relationships

None.

## Related content

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create programControl](https://learn.microsoft.com/en-us/graph/api/programcontrol-create?view=graph-rest-beta) | [programControl](https://learn.microsoft.com/en-us/graph/api/resources/programcontrol?view=graph-rest-beta) | Add a programControl to a program. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
 "id": "string (identifier)",
 "displayName": "string"
}
```
