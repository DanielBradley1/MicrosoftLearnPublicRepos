<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-skypeforbusinessbaseauditrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# skypeForBusinessBaseAuditRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a base audit record type for Skype for Business activities. This resource serves as the parent type for more specific Skype for Business audit records, providing common properties and structures used across different types of Skype for Business audit events. Specific child types extend this base type to capture particular categories of Skype for Business activities.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.skypeForBusinessBaseAuditRecord"
}
```
