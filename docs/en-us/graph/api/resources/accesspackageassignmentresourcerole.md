<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentresourcerole?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# accessPackageAssignmentResourceRole resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-beta), an access package assignment resource role indicates the resource-specific role that a subject is assigned through an access package assignment.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentresourcerole-get?view=graph-rest-beta) | [accessPackageAssignmentResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentresourcerole?view=graph-rest-beta) | Retrieve an accessPackageAssignmentResourceRole object. |
| [List](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-list-accesspackageassignmentresourceroles?view=graph-rest-beta) | [accessPackageAssignmentResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentresourcerole?view=graph-rest-beta) collection | Retrieve a list of accessPackageAssignmentResourceRole objects. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Read-only. |
| originId | String | A unique identifier relative to the origin system, corresponding to the originId property of the [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-beta). |
| originSystem | String | The system where the role assignment is to be created or has been created for an access package assignment, such as `SharePointOnline`, `AadGroup`, or `AadApplication`, corresponding to the originSystem property of the [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-beta). |
| status | String | The value is `PendingFulfillment` before the access package assignment is delivered to the origin system, and `Fulfilled` after the access package assignment is delivered to the origin system. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| accessPackageAssignments | [accessPackageAssignment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignment?view=graph-rest-beta) collection | The access package assignments resulting in this role assignment. Read-only. Nullable. |
| accessPackageResourceRole | [accessPackageResourceRole](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcerole?view=graph-rest-beta) | Read-only. Nullable. |
| accessPackageResourceScope | [accessPackageResourceScope](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourcescope?view=graph-rest-beta) | Read-only. Nullable. |
| accessPackageSubject | [accessPackageSubject](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesubject?view=graph-rest-beta) | Read-only. Nullable. Supports `$filter` \(`eq`\) on **objectId** and `$expand` query parameters. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "originId": "String",
  "originSystem": "String",
  "status": "String"
}
```
