<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/logicapptriggerendpointconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# logicAppTriggerEndpointConfiguration resource type

Namespace: microsoft.graph

The configuration details for the logic app's endpoint. Derived from the [customExtensionEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionendpointconfiguration?view=graph-rest-1.0) abstract type.

This object is configured in the **endpointConfiguration** property of the [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| logicAppWorkflowName | String | The name of the logic app. |
| resourceGroupName | String | The Azure resource group name for the logic app. |
| subscriptionId | String | Identifier of the Azure subscription for the logic app. |
| url | String | The URL to the logic app endpoint that will be triggered. Only required for app-only token scenarios where app is creating a [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0) without a signed-in user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.logicAppTriggerEndpointConfiguration",
  "subscriptionId": "String",
  "resourceGroupName": "String",
  "logicAppWorkflowName": "String",
  "url": "String"
}
```
