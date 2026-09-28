<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-microsoftdefenderexpertsbaseauditrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# microsoftDefenderExpertsBaseAuditRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a base audit record type for Microsoft Defender Experts service activities. This abstract record type serves as the parent class for more specific audit records related to Microsoft Defender Experts services, providing common properties and functionality for tracking security monitoring and managed threat hunting activities performed by Microsoft security experts on behalf of an organization.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.microsoftDefenderExpertsBaseAuditRecord"
}
```
