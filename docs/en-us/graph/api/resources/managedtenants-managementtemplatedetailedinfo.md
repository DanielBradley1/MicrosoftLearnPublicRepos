<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementtemplatedetailedinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# managementTemplateDetailedInfo resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents detailed information for the management template.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | managementCategory | The management category for the management template. The possible values are: `custom`, `devices`, `identity`, `unknownFutureValue`. Required. Read-only. |
| displayName | String | The display name for the management template. Required. Read-only. |
| managementTemplateId | String | The unique identifier for the management template. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managementTemplateDetailedInfo",
  "managementTemplateId": "String",
  "displayName": "String",
  "category": "String"
}
```
