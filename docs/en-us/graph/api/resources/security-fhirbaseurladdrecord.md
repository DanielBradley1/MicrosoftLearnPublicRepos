<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-fhirbaseurladdrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# fhirBaseUrlAddRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record that captures FHIR base URL addition operations in healthcare environments. This record type documents when an administrator or authorized user adds a new Fast Healthcare Interoperability Resources \(FHIR\) base URL to the system. FHIR is a standard for healthcare data exchange, and these audit records help healthcare organizations track the configuration of FHIR endpoints for compliance with healthcare regulations and security monitoring.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.fhirBaseUrlAddRecord"
}
```
