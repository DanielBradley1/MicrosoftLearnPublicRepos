<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# auditData resource type

Namespace: microsoft.graph.security

An abstract type that represents audit log data in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-1.0). This base type is inherited by over 300 derived types, each representing audit data for a specific Microsoft 365 service or feature. For a complete list of all derived types, see [auditData derived types](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata-derived-types?view=graph-rest-1.0).

The [defaultAuditData](https://learn.microsoft.com/en-us/graph/api/resources/security-defaultauditdata?view=graph-rest-1.0) type is an open type that contains the raw JSON audit data for Microsoft 365 services that don't have a specific derived type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dynamicProperties | [microsoft.graph.security.auditRecordTypeDictionary](https://learn.microsoft.com/en-us/graph/api/resources/security-auditrecordtypedictionary?view=graph-rest-1.0) | An open-type dictionary that contains dynamic audit event properties as name-value pairs. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.auditData",
  "dynamicProperties": {
    "@odata.type": "microsoft.graph.security.auditRecordTypeDictionary"
  }
}
```
