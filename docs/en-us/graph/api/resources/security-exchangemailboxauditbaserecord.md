<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-exchangemailboxauditbaserecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# exchangeMailboxAuditBaseRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a base type for Exchange mailbox audit records that capture mailbox access and operations. This resource serves as the foundation for more specific mailbox audit record types and provides common properties for tracking user activities within Exchange mailboxes. It helps organizations monitor mailbox access patterns, detect suspicious activities, and maintain compliance with data protection requirements.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.exchangeMailboxAuditBaseRecord"
}
```
