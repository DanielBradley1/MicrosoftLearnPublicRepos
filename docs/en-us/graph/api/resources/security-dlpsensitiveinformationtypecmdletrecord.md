<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-dlpsensitiveinformationtypecmdletrecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# dlpSensitiveInformationTypeCmdletRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record that captures administrative cmdlet operations related to DLP sensitive information types. This record type documents actions taken by administrators when creating, modifying, or managing Data Loss Prevention \(DLP\) sensitive information type definitions through PowerShell cmdlets. These records help track changes to the organization's data classification patterns used for content scanning and policy enforcement.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.dlpSensitiveInformationTypeCmdletRecord"
}
```
