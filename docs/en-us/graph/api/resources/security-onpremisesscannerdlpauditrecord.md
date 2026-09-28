<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-onpremisesscannerdlpauditrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# onPremisesScannerDlpAuditRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record that captures information about general on-premises scanner Data Loss Prevention \(DLP\) activities. This resource provides details about scanner operations, configuration changes, and system-level events related to the deployment and management of on-premises DLP scanning infrastructure. These audit records help organizations track the health, performance, and administration of their on-premises content scanning solutions integrated with Microsoft information protection services.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.onPremisesScannerDlpAuditRecord"
}
```
