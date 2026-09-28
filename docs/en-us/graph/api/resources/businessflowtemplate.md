<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/businessflowtemplate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-22 -->

# businessFlowTemplate resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

This version of the access review API is deprecated and will stop returning data on May 19, 2023. Please use [access reviews API](https://learn.microsoft.com/en-us/graph/api/resources/accessreviewsv2-overview?view=graph-rest-beta&preserve-view=true).

In the Microsoft Entra [access reviews](https://learn.microsoft.com/en-us/graph/api/resources/accessreviews-root?view=graph-rest-beta) feature, the **businesFlowTemplate** represents a Microsoft Entra business flow template. The identifier of a template, such as to review guest members of a group, is supplied by the caller when creating an access review.

The business flow template objects are predefined and automatically generated when an authorized administrator onboards the tenant to use the access reviews feature. They include the following access reviews workflows and scopes:

- Assignments to an application
- Memberships of a group
- Memberships of a Microsoft Entra role
- Memberships of guests to a group
- Assignments of guests to an application.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/businessflowtemplate-list?view=graph-rest-beta) | [businessFlowTemplate](https://learn.microsoft.com/en-us/graph/api/resources/businessflowtemplate?view=graph-rest-beta) collection | Get the business flow templates appropriate to access reviews. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The feature-assigned identifier of the business flow template. These values are case sensitive. |
| displayName | String | The name of the business flow template |

## Relationships

None.

## Related content

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Create accessReview](https://learn.microsoft.com/en-us/graph/api/accessreview-create?view=graph-rest-beta) | [accessReview](https://learn.microsoft.com/en-us/graph/api/resources/accessreview?view=graph-rest-beta) | Create a new accessReview. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
 "id": "string (identifier)",
 "displayName": "string"
}
```
