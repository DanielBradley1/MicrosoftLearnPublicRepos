<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-comment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# comment resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a human-authored comment in a case activity timeline.

For cast segments in URLs, use the full type name, for example `microsoft.graph.security.caseManagement.comment`.

Inherited from [activity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activity?view=graph-rest-beta).

## Methods

This resource is part of a polymorphic collection managed by the [activity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activity?view=graph-rest-beta) base type. Use the activity endpoints to [create](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-post-activities?view=graph-rest-beta), [get](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-activity-get?view=graph-rest-beta), [update](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-activity-update?view=graph-rest-beta), and [delete](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-activity-delete?view=graph-rest-beta) comment activities.

Updating and deleting comment activities isn't supported for [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta) objects.

To use a supported query option with a property declared only on **comment**, cast the base activities collection to `microsoft.graph.security.caseManagement.comment`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The user or service that created the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| createdDateTime | DateTimeOffset | The date and time when the resource was created. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| id | String | The unique identifier for the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter`. |
| lastModifiedBy | String | The user or service that last modified the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| message | String | The comment body. Supports `$filter`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.comment",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "message": "String"
}
```
