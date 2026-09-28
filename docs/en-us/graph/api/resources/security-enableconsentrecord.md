<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-enableconsentrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# enableConsentRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record for operations that enable user consent for applications. This record type documents when administrators enable the ability for users to grant consent to applications to access organizational data. The record includes details about who made the change, when it occurred, and the scope of the consent permissions allowed. Tracking these events is important for security monitoring and compliance reporting.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.enableConsentRecord"
}
```
