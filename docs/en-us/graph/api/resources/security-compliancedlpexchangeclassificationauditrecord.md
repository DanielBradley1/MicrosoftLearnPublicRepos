<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-compliancedlpexchangeclassificationauditrecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-14 -->

# complianceDLPExchangeClassificationAuditRecord resource type

Namespace: microsoft.graph.security

Represents an audit record for Compliance DLP Exchange classification events. This resource captures information about these activities as part of the Microsoft 365 unified audit log.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-1.0). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-1.0).

## Methods

None. This resource is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dynamicProperties | [microsoft.graph.security.auditRecordTypeDictionary](https://learn.microsoft.com/en-us/graph/api/resources/security-auditrecordtypedictionary?view=graph-rest-1.0) | Inherited from [auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.complianceDLPExchangeClassificationAuditRecord",
  "dynamicProperties": {
    "@odata.type": "microsoft.graph.security.auditRecordTypeDictionary"
  }
}
```
