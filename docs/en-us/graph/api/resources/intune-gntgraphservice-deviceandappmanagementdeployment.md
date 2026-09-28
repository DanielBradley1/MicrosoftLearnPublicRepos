<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeployment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# deviceAndAppManagementDeployment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents a device and app management deployment for staged rollout scenarios.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceAndAppManagementDeployments](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeployment-list?view=graph-rest-beta) | [deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeployment?view=graph-rest-beta) collection | List properties and relationships of the [deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeployment?view=graph-rest-beta) objects. |
| [Get deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeployment-get?view=graph-rest-beta) | [deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeployment?view=graph-rest-beta) | Read properties and relationships of the [deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeployment?view=graph-rest-beta) object. |
| [Create deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeployment-create?view=graph-rest-beta) | [deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeployment?view=graph-rest-beta) | Create a new [deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeployment?view=graph-rest-beta) object. |
| [Delete deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeployment-delete?view=graph-rest-beta) | None | Deletes a [deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeployment?view=graph-rest-beta). |
| [Update deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeployment-update?view=graph-rest-beta) | [deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeployment?view=graph-rest-beta) | Update the properties of a [deviceAndAppManagementDeployment](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeployment?view=graph-rest-beta) object. |
| [deployAction action](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeployment-deployaction?view=graph-rest-beta) | Boolean |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key for the resource. |
| deploymentPlanId | String | Key of the device and app management deployment plan. |
| displayName | String | The display name of the deployment plan. |
| description | String | The description of the deployment plan. |
| payloads | [deviceAndAppManagementDeploymentPayload](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentpayload?view=graph-rest-beta) collection | The payloads associated with the device and app management deployment. |
| createdDateTime | DateTimeOffset | The date and time of when the deployment was created \(UTC\). |
| lastModifiedDateTime | DateTimeOffset | The date and time of when the plan was last modified \(UTC\). |
| mode | [deviceAndAppManagementDeploymentMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentmode?view=graph-rest-beta) | Indicates the device and app management deployment mode. Possible values are: `draft`, `active`, `unknownFutureValue`. |
| state | [deviceAndAppManagementDeploymentState](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentstate?view=graph-rest-beta) | Indicates the device and app management deployment state. Possible values are: `notStarted`, `inProgress`, `canceled`, `paused`, `completed`, `error`, `unknownFutureValue`. |
| ringCount | Int32 | The number of rings in the deployment. |
| startDateTime | DateTimeOffset | The start date and time of the deployment \(UTC\). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| rings | [deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentring?view=graph-rest-beta) collection | The deployment rings associated with the device and app management deployment. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementDeployment",
  "id": "String (identifier)",
  "deploymentPlanId": "String",
  "displayName": "String",
  "description": "String",
  "payloads": [
    {
      "@odata.type": "microsoft.graph.deviceAndAppManagementDeploymentPayload",
      "payloadId": "String",
      "payloadDisplayName": "String",
      "payloadType": "String"
    }
  ],
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "mode": "String",
  "state": "String",
  "ringCount": 1024,
  "startDateTime": "String (timestamp)"
}
```
