<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-cpspolicyconfigauditrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# cpsPolicyConfigAuditRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record for policy configuration changes in the Customer Protection Service \(CPS\). This resource captures detailed audit information about modifications to policy configurations, including creation, updates, and deletions of policy settings related to customer protection.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.cpsPolicyConfigAuditRecord"
}
```
