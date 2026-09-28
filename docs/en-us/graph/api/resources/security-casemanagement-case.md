<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-15 -->

# case resource type \(case management\)

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract security case that tracks an investigation and organizes related tasks, activities, relations, and attachments. Use the [genericCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-genericcase?view=graph-rest-beta) derived type to create case instances. You can't create [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta) instances with API requests; incident cases are created by the service. Instances are differentiated by `@odata.type`. This is an abstract type.

For cast segments in URLs, use the full type name, for example `microsoft.graph.security.caseManagement.genericCase` or `microsoft.graph.security.caseManagement.incidentCase`.

Inherits from [microsoft.graph.security.caseManagement.caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta).

## Methods

Use the [Update](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-update?view=graph-rest-beta) method to update **displayName** and **status** for all case types. Other mutable properties depend on the concrete case type.

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-casemanagementroot-list-cases?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) collection | List security cases. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-casemanagementroot-post-cases?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) | Create a security case by specifying a supported derived type in `@odata.type`. The [incidentCase](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-incidentcase?view=graph-rest-beta) derived type isn't supported for create requests. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-get?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) | Read the properties and relationships of a security case. |
| [Update](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-case-update?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta) | Update the supported mutable properties of a security case. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-casemanagementroot-delete-cases?view=graph-rest-beta) | None | Delete a security case. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | The user or service that created the case. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter` and `$orderby`. |
| createdDateTime | DateTimeOffset | The date and time when the case was created. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter` and `$orderby`. |
| customFields | [microsoft.graph.security.caseManagement.customFieldValues](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldvalues?view=graph-rest-beta) | Tenant-defined custom field values keyed by the exact **displayName** of each custom field definition. The property and its dynamic fields don't support `$filter`. |
| displayName | String | The display name of the case. Supports `$filter` and `$orderby`. |
| id | String | The unique identifier for the case. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` and `$orderby`. |
| lastModifiedBy | String | The user or service that last modified the case. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter` and `$orderby`. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the case was last modified. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter` and `$orderby`. |
| slaPolicies | [microsoft.graph.security.caseManagement.caseSlaPolicyEntry](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-caseslapolicyentry?view=graph-rest-beta) collection | A denormalized, read-only collection of SLA \(service level agreement\) policy status entries for the case. Each entry represents one SLA policy applied to the case, including its current status and breach target time. Computed by the service; any value supplied in a create or update request is silently ignored. Supports `$filter` using the `any()` lambda operator only, for example, `$filter=slaPolicies/any(p: p/status eq 'breached')`. The `all()` lambda operator and other collection functions aren't supported. Doesn't support `$orderby`. |
| status | String | The tenant-defined lifecycle status of the case. Use a **displayName** value returned in the status tree by [List statuses](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-statuses?view=graph-rest-beta) from `/security/caseManagement/caseTypeConfigurations/genericCase/statuses` or `/security/caseManagement/caseTypeConfigurations/incidentCase/statuses`, depending on the case type. Supports `$filter` \(`eq`\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| activities | [microsoft.graph.security.caseManagement.activity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activity?view=graph-rest-beta) collection | The timeline of comments and audit events associated with the case. Supports `$expand`. |
| attachments | [microsoft.graph.security.caseManagement.attachment](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-attachment?view=graph-rest-beta) collection | Evidence files and metadata associated with the case. Supports `$expand`. |
| relations | [microsoft.graph.security.caseManagement.relation](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-relation?view=graph-rest-beta) collection | Links from the case to related security resources. Supports `$expand`. |
| tasks | [microsoft.graph.security.caseManagement.task](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-task?view=graph-rest-beta) collection | Tasks used to track work required to resolve the case. Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.case",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "displayName": "String",
  "status": "String",
  "customFields": {"@odata.type": "#microsoft.graph.security.caseManagement.customFieldValues"},
  "slaPolicies": [
    {"@odata.type": "microsoft.graph.security.caseManagement.caseSlaPolicyEntry"}
  ]
}
```
