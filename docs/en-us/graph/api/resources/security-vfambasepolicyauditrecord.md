<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-vfambasepolicyauditrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# vfamBasePolicyAuditRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record for Virtual Filtering Access Management \(VFAM\) base policy operations. This resource captures activities related to the base configuration of VFAM policies, which manage network filtering and access controls. The audit data helps security administrators track changes to foundational security policies that control network traffic filtering, access permissions, and security boundaries within the organization's environment.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.vfamBasePolicyAuditRecord"
}
```
