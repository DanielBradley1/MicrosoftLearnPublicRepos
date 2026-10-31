<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-cloudsecuritymanagement?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# cloudSecurityManagement resource type

Namespace: microsoft.graph.security

Audit data for Cloud Security Management events returned in the **auditData** property of an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-1.0).

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-1.0).

This resource is an open type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dynamicProperties | [microsoft.graph.security.auditRecordTypeDictionary](https://learn.microsoft.com/en-us/graph/api/resources/security-auditrecordtypedictionary?view=graph-rest-1.0) | An open-type dictionary that contains dynamic audit event properties as name-value pairs. Inherited from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.cloudSecurityManagement",
  "dynamicProperties": {
    "@odata.type": "microsoft.graph.security.auditRecordTypeDictionary"
  }
}
```
