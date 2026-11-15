<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-systemdata?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# systemData resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains creation and modification provenance for the **systemData** property of a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdBy | String | Identifier of the identity that created the connection. |
| createdByType | String | Type of identity that created the connection. |
| createdDateTime | DateTimeOffset | UTC resource creation time. |
| lastModifiedBy | String | Identifier of the identity that last modified the connection. |
| lastModifiedByType | String | Type of identity that last modified the connection. |
| lastModifiedDateTime | DateTimeOffset | UTC time of the last effective modification. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.systemData",
  "createdDateTime": "String (timestamp)",
  "createdBy": "String",
  "createdByType": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "lastModifiedBy": "String",
  "lastModifiedByType": "String"
}
```
