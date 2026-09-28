<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-genericcase?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# genericCase resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a generic case with assignment, priority, due date, and closing notes. This resource derives from [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) and participates in the polymorphic `/security/caseManagement/cases` collection.

For cast segments in URLs, use the full type name, for example `microsoft.graph.security.caseManagement.genericCase`.

## Methods

This resource is part of a polymorphic collection managed by the [case resource](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) base type. Operations are performed through the base type endpoints.

Use the base type [Update](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-update?view=graph-rest-beta) method to update **assignedTo**, **closingNotes**, **description**, **displayName**, **dueDateTime**, **priority**, and **status**.

To use a supported query option with a property declared only on **genericCase**, cast the base cases collection to `microsoft.graph.security.caseManagement.genericCase`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| assignedTo | String | The user assigned to the generic case. Supports `$filter` and `$orderby`. |
| closingNotes | String | Notes recorded when the generic case is closed. Supports `$filter`. |
| createdBy | String | The user or service that created the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter` and `$orderby`. |
| createdDateTime | DateTimeOffset | The date and time when the resource was created. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter` and `$orderby`. |
| customFields | [microsoft.graph.security.caseManagement.customFieldValues](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldvalues?view=graph-rest-beta) | Tenant-defined custom field values keyed by the exact **displayName** of each custom field definition. The property and its dynamic fields don't support `$filter`. Inherited from [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta). |
| description | String | The description of the generic case. Supports `$filter`. |
| displayName | String | The display name of the generic case. Inherited from [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta). Supports `$filter` and `$orderby`. |
| dueDateTime | DateTimeOffset | The target completion date and time for the generic case. Supports `$filter`. |
| id | String | The unique identifier for the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` and `$orderby`. |
| lastModifiedBy | String | The user or service that last modified the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter` and `$orderby`. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter` and `$orderby`. |
| priority | String | The priority assigned to the generic case. Possible values are: `veryLow`, `low`, `medium`, `high`, and `critical`. Supports `$filter`. |
| status | String | The tenant-defined lifecycle status of the generic case. Use a **displayName** value returned in the status tree by [List statuses](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-statuses?view=graph-rest-beta) from `/security/caseManagement/caseTypeConfigurations/genericCase/statuses`. Inherited from [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta). Supports `$filter` \(`eq`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activities | [microsoft.graph.security.caseManagement.activity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activity?view=graph-rest-beta) collection | The timeline of comments and audit events associated with the case. Inherited from [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta). |
| attachments | [microsoft.graph.security.caseManagement.attachment](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachment?view=graph-rest-beta) collection | Evidence files and metadata associated with the case. Inherited from [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta). |
| relations | [microsoft.graph.security.caseManagement.relation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta) collection | Links from the case to related security resources. Inherited from [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta). |
| tasks | [microsoft.graph.security.caseManagement.task](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta) collection | Tasks used to track work required to resolve the case. Inherited from [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.genericCase",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "displayName": "String",
  "status": "String",
  "customFields": {"@odata.type": "#microsoft.graph.security.caseManagement.customFieldValues"},
  "description": "String",
  "closingNotes": "String",
  "assignedTo": "String",
  "priority": "String",
  "dueDateTime": "String (timestamp)"
}
```
