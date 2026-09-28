<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# activity resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract activity that records an update in a security [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) timeline. Use the derived [comment](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-comment?view=graph-rest-beta) and [auditLog](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-auditlog?view=graph-rest-beta) resources to work with specific activity records. Create, update, and delete operations are supported for comments; audit logs support get operations only.

For cast segments in URLs, use the full type name, for example `microsoft.graph.security.caseManagement.comment`.

This resource inherits from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-list-activities?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.activity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activity?view=graph-rest-beta) collection | Get a list of timeline activities for a case. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-post-activities?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.activity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activity?view=graph-rest-beta) | Create a comment activity for a case. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-activity-get?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.activity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activity?view=graph-rest-beta) | Read the properties and relationships of an activity. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-activity-update?view=graph-rest-beta) | None | Update a comment activity. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-activity-delete?view=graph-rest-beta) | None | Delete a comment activity. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The user or service that created the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when the resource was created. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| id | String | The unique identifier for the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | String | The user or service that last modified the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.activity",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String"
}
```
