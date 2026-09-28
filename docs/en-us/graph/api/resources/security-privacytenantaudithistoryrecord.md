<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-privacytenantaudithistoryrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# privacyTenantAuditHistoryRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record that tracks tenant-level privacy management activities and configuration changes. This resource provides details about administrative actions taken to configure privacy settings, policy changes, and other tenant-wide privacy management activities. These audit records help organizations maintain a historical record of privacy management decisions and configurations for compliance and governance purposes.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.privacyTenantAuditHistoryRecord"
}
```
