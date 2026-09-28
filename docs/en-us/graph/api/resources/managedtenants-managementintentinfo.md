<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementintentinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# managementIntentInfo resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents relationship information for a management intent.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| managementIntentDisplayName | String | The display name for the management intent. Optional. Read-only. |
| managementIntentId | String | The identifier for the management intent. Required. Read-only. |
| managementTemplates | [microsoft.graph.managedTenants.managementTemplateDetailedInfo](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementtemplatedetailedinfo?view=graph-rest-beta) collection | The collection of management template information associated with the management intent. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managementIntentInfo",
  "managementIntentId": "String",
  "managementIntentDisplayName": "String",
  "managementTemplates": [
    {
      "@odata.type": "microsoft.graph.managedTenants.managementTemplateDetailedInfo"
    }
  ]
}
```
