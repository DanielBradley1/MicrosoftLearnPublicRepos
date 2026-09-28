<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# operationalInsightsConnection resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a specialized [resourceConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-resourceconnection?view=graph-rest-beta) that links a Log Analytics workspace to Windows Autopatch.

Inherits from [resourceConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-resourceconnection?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-list-resourceconnections-operationalinsightsconnection?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.operationalInsightsConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta) collection | Get a list of the [operationalInsightsConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/adminwindowsupdates-post-resourceconnections-operationalinsightsconnection?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.operationalInsightsConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta) | Create a new [operationalInsightsConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/windowsupdates-operationalinsightsconnection-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.operationalInsightsConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta) | Read the properties and relationships of an [operationalInsightsConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta) object. |
| [Delete operational insights connection](https://learn.microsoft.com/en-us/graph/api/windowsupdates-operationalinsightsconnection-delete?view=graph-rest-beta) | None | Delete an [operationalInsightsConnection](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-operationalinsightsconnection?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| azureResourceGroupName | String | The name of the Azure resource group that contains the Log Analytics workspace. |
| azureSubscriptionId | String | The Azure subscription ID that contains the Log Analytics workspace. |
| id | String | An identifier for the resource connection. Key. Not nullable. Read-only. Returned by default. |
| state | microsoft.graph.windowsUpdates.resourceConnectionState | The state of the connection. The possible values are: `connected`, `notAuthorized`, `notFound`, `unknownFutureValue`. |
| workspaceName | String | The name of the Log Analytics workspace. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.operationalInsightsConnection",
  "azureResourceGroupName": "String",  
  "azureSubscriptionId": "String",
  "id": "String (identifier)",
  "state": "String",
  "workspaceName": "String"
}
```
