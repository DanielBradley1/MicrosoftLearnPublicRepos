<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-auditcoreroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-14 -->

# auditCoreRoot resource type

Namespace: microsoft.graph.security

Represents the entry point for the audit log query API in Microsoft Graph. Use this resource to access audit log records through the **queries** navigation property.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List audit log queries](https://learn.microsoft.com/en-us/graph/api/security-auditcoreroot-list-auditlogqueries?view=graph-rest-1.0) | [auditLogQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogquery?view=graph-rest-1.0) collection | Get a list of the [auditLogQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogquery?view=graph-rest-1.0) objects and their properties. |
| [Create audit log query](https://learn.microsoft.com/en-us/graph/api/security-auditcoreroot-post-auditlogqueries?view=graph-rest-1.0) | [auditLogQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogquery?view=graph-rest-1.0) | Create a new [auditLogQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogquery?view=graph-rest-1.0) object. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| queries | [microsoft.graph.security.auditLogQuery](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogquery?view=graph-rest-1.0) collection | The collection of audit log queries. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.auditCoreRoot"
}
```
