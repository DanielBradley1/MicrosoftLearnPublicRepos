<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogquery?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# auditLogQuery resource type

Namespace: microsoft.graph.security

Represents a query against the Microsoft 365 unified audit log. Use this resource to define search parameters and retrieve audit log records.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get audit log query](https://learn.microsoft.com/en-us/graph/api/security-auditlogquery-get?view=graph-rest-1.0) | [auditLogQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogquery?view=graph-rest-1.0) | Read the properties and relationships of an [auditLogQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogquery?view=graph-rest-1.0) object. |
| [List records](https://learn.microsoft.com/en-us/graph/api/security-auditlogquery-list-records?view=graph-rest-1.0) | [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-1.0) collection | Get the auditLogRecord resources from the records navigation property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| administrativeUnitIdFilters | String collection | The collection of administrative unit IDs to filter on. |
| displayName | String | The display name of the audit log query. |
| filterEndDateTime | DateTimeOffset | The end date and time of the audit log query filter. |
| filterStartDateTime | DateTimeOffset | The start date and time of the audit log query filter. |
| id | String | The unique identifier for the audit log query. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| ipAddressFilters | String collection | The collection of IP addresses to filter on. |
| keywordFilter | String | The keyword to filter on. |
| objectIdFilters | String collection | The collection of object IDs to filter on. |
| operationFilters | String collection | The collection of operations to filter on. |
| recordTypeFilters | [microsoft.graph.security.auditLogRecordType](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecordtype?view=graph-rest-1.0) collection | The collection of record types to filter on. |
| serviceFilters | String collection | The collection of services to filter on. |
| status | microsoft.graph.security.auditLogQueryStatus | The status of the audit log query. Possible values are: `notStarted`, `running`, `succeeded`, `failed`, `cancelled`, `unknownFutureValue`. |
| userPrincipalNameFilters | String collection | The collection of user principal names to filter on. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| records | [microsoft.graph.security.auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-1.0) collection | The collection of audit log records retrieved by the query. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.auditLogQuery",
  "id": "String (identifier)",
  "displayName": "String",
  "filterStartDateTime": "String (timestamp)",
  "filterEndDateTime": "String (timestamp)",
  "recordTypeFilters": ["String"],
  "keywordFilter": "String",
  "serviceFilters": ["String"],
  "operationFilters": ["String"],
  "userPrincipalNameFilters": ["String"],
  "ipAddressFilters": ["String"],
  "objectIdFilters": ["String"],
  "administrativeUnitIdFilters": ["String"],
  "status": "String"
}
```
