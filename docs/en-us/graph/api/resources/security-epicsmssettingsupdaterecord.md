<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-epicsmssettingsupdaterecord?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-09 -->

# epicSMSSettingsUpdateRecord resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an audit record that captures updates to Epic SMS configuration settings in healthcare environments. This record type documents when an administrator or authorized user modifies settings related to the SMS messaging service integrated with Epic healthcare systems. The audit information includes details about the specific settings changed, who made the changes, and when they occurred, helping healthcare organizations maintain compliance with security and privacy regulations.

Inherits from [microsoft.graph.security.auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-beta). The audit data for this record type is returned as the **auditData** property in an [auditLogRecord](https://learn.microsoft.com/en-us/graph/api/resources/security-auditlogrecord?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.epicSMSSettingsUpdateRecord"
}
```
