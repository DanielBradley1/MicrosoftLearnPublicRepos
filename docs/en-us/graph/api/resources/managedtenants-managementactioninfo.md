<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-managementactioninfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# managementActionInfo resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents reference information for a management action.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| managementActionId | String | The identifier for the management action. Required. Read-only. |
| managementTemplateId | String | The identifier for the management template. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.managementActionInfo",
  "managementTemplateId": "String",
  "managementActionId": "String"
}
```
