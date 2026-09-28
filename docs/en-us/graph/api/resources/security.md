<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# security resource type

Namespace: microsoft.graph

The security resource is the entry point for the Security object model. It returns a singleton security resource. It doesn't contain any usable properties.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Run hunting query](https://learn.microsoft.com/en-us/graph/api/security-security-runhuntingquery?view=graph-rest-1.0) | [microsoft.graph.security.huntingQueryResults](https://learn.microsoft.com/en-us/graph/api/resources/security-huntingqueryresults?view=graph-rest-1.0) | Queries a specified set of event, activity, or entity data supported by Microsoft 365 Defender to proactively look for specific threats in your environment. |

## Properties

None

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| alerts | [alert](https://learn.microsoft.com/en-us/graph/api/resources/alert?view=graph-rest-1.0) collection | Read-only. Nullable. |
| alerts\_v2 | [microsoft.graph.security.alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0) collection | A collection of alerts in Microsoft 365 Defender. |
| auditLog | [microsoft.graph.security.auditCoreRoot](https://learn.microsoft.com/en-us/graph/api/resources/security-auditcoreroot?view=graph-rest-1.0) | The entry point for the audit log query API. |
| data security and compliance | [microsoft.graph.tenantDataSecurityAndGovernance](https://learn.microsoft.com/en-us/graph/api/resources/tenantdatasecurityandgovernance?view=graph-rest-1.0) | A container for Microsoft Purview data security and compliance APIs. |
| identities | [microsoft.graph.security.identityContainer](https://learn.microsoft.com/en-us/graph/api/resources/security-identitycontainer?view=graph-rest-1.0) | A container for security identities APIs. |
| incidents | [microsoft.graph.security.incident](https://learn.microsoft.com/en-us/graph/api/resources/security-incident?view=graph-rest-1.0) collection | A collection of incidents in Microsoft 365 Defender, each of which is a set of correlated alerts and associated metadata that reflects the story of an attack. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
}
```

## Example

The **security** resource is available at the root of the graph.

```http
GET https://graph.microsoft.com/v1.0/security
```

```http
HTTP/1.1 200 OK
Content-type: application/json

{
}
```
