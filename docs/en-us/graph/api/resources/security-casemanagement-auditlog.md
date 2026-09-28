<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-auditlog?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# auditLog resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit event that records a change or action in a case.

For cast segments in URLs, use the full type name, for example `microsoft.graph.security.caseManagement.auditLog`.

Inherited from [activity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activity?view=graph-rest-beta).

## Methods

This resource is part of a polymorphic collection managed by the [activity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activity?view=graph-rest-beta) base type. Use the [Get activity](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-activity-get?view=graph-rest-beta) endpoint to read audit log activities. Create, update, and delete operations aren't supported for audit logs.

To use a supported query option with a property declared only on **auditLog**, cast the base activities collection to `microsoft.graph.security.caseManagement.auditLog`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [microsoft.graph.security.caseManagement.auditAction](#auditaction-values) | The action represented by the audit log activity. Supports `$filter`. |
| createdBy | String | The user or service that created the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| createdDateTime | DateTimeOffset | The date and time when the resource was created. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| details | [microsoft.graph.security.caseManagement.activityResourceDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-activityresourcedetails?view=graph-rest-beta) | The target resource details for the audit activity. |
| id | String | The unique identifier for the resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter`. |
| lastModifiedBy | String | The user or service that last modified the resource. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the resource was last modified. Inherited from [caseManagementEntity](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casemanagemententity?view=graph-rest-beta). Supports `$filter`. |
| modifiedProperties | [microsoft.graph.security.caseManagement.modifiedProperty](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-modifiedproperty?view=graph-rest-beta) collection | The collection of property changes recorded in the audit log. Supports `$filter`. |

### auditAction values

| Member | Description |
| :--- | :--- |
| link | A resource was linked to the case. |
| unlink | A resource was unlinked from the case. |
| update | A resource was updated. |
| delete | A resource was deleted. |
| create | A resource was created. |
| upload | A file was uploaded. |
| download | A file was downloaded. |
| fileUploadMalwareDetected | Malware was detected during file upload. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.auditLog",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "action": "String",
  "details": {"@odata.type": "#microsoft.graph.security.caseManagement.activityResourceDetails"},
  "modifiedProperties": [{"@odata.type": "#microsoft.graph.security.caseManagement.modifiedProperty"}]
}
```
