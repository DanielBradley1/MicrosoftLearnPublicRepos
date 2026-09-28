<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-uploadcertificaterecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# uploadCertificateRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record for certificate upload operations in Microsoft security services. This resource captures activities related to the uploading of security certificates into the system, including who uploaded certificates, when they were uploaded, certificate properties, and the success or failure status of the upload operation. The audit data helps security administrators track changes to certificate configurations, which are critical components of encryption, authentication, and secure communications infrastructure.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.uploadCertificateRecord"
}
```
