<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-14 -->

# auditData resource type

Namespace: microsoft.graph.security

An abstract type that supports the audit logs of various Microsoft 365 services like [defaultAuditData](https://learn.microsoft.com/en-us/graph/api/resources/security-defaultauditdata?view=graph-rest-1.0), which contains the JSON files of these Microsoft 365 services.

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
