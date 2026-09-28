<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-defendersecurityalertbaserecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# defenderSecurityAlertBaseRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a base type for Microsoft Defender security alert audit records. This resource serves as the foundation for more specific security alert record types and captures common properties related to security threats and incidents detected by Microsoft Defender security solutions. It provides the core structure for tracking and auditing security alerts across different workloads and environments.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.defenderSecurityAlertBaseRecord"
}
```
