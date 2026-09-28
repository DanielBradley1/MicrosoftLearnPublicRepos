<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-mipautolabelpolicyauditrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# mipAutoLabelPolicyAuditRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record that captures activities related to automatic sensitivity labeling policy management. This record type documents events such as creating, modifying, or deleting auto-labeling policies, changing policy scope, adjusting content scanning rules, and modifying label application settings, providing visibility into how automated information protection policies are configured and managed.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.mipAutoLabelPolicyAuditRecord"
}
```
