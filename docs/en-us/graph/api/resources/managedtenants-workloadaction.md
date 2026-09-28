<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-workloadaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# workloadAction resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an action that will be performed for a specific workload.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionId | String | The unique identifier for the workload action. Required. Read-only. |
| category | workloadActionCategory | The category for the workload action. The possible values are: `automated`, `manual`, `unknownFutureValue`. Optional. Read-only. |
| description | String | The description for the workload action. Optional. Read-only. |
| displayName | String | The display name for the workload action. Optional. Read-only. |
| service | String | The service associated with workload action. Optional. Read-only. |
| settings | [microsoft.graph.managedTenants.setting](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-setting?view=graph-rest-beta) collection | The collection of settings associated with the workload action. Optional. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.workloadAction",
  "actionId": "String",
  "category": "String",
  "displayName": "String",
  "description": "String",
  "service": "String",
  "settings": [
    {
      "@odata.type": "microsoft.graph.managedTenants.setting"
    }
  ]
}
```
