<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-smsdeletephonenumberrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# smsDeletePhoneNumberRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record that captures SMS phone number deletion activities. This resource tracks events where phone numbers are removed or deregistered from SMS messaging services within Microsoft services, such as those used for multi-factor authentication, notifications, or alerts. These audit records help organizations monitor changes to their SMS communication channels for security and authentication purposes, providing visibility into when and why phone numbers are being removed.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.smsDeletePhoneNumberRecord"
}
```
