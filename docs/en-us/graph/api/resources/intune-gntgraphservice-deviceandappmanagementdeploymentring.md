<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentring?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# deviceAndAppManagementDeploymentRing resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Device and app management deployment ring with status data.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceAndAppManagementDeploymentRings](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeploymentring-list?view=graph-rest-beta) | [deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentring?view=graph-rest-beta) collection | List properties and relationships of the [deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentring?view=graph-rest-beta) objects. |
| [Get deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeploymentring-get?view=graph-rest-beta) | [deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentring?view=graph-rest-beta) | Read properties and relationships of the [deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentring?view=graph-rest-beta) object. |
| [Create deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeploymentring-create?view=graph-rest-beta) | [deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentring?view=graph-rest-beta) | Create a new [deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentring?view=graph-rest-beta) object. |
| [Delete deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeploymentring-delete?view=graph-rest-beta) | None | Deletes a [deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentring?view=graph-rest-beta). |
| [Update deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeploymentring-update?view=graph-rest-beta) | [deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentring?view=graph-rest-beta) | Update the properties of a [deviceAndAppManagementDeploymentRing](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentring?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key for the resource. |
| displayName | String | The display name of the deployment ring. |
| order | Int32 | The order in which this ring should be processed relative to other rings. |
| activationCriteria | [deviceAndAppManagementRingActivationCriteria](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringactivationcriteria?view=graph-rest-beta) | The criteria that must be met for current deployment ring activation. |
| state | [deviceAndAppManagementDeploymentRingState](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentringstate?view=graph-rest-beta) | Device and app management deployment ring status. Possible values are: `notActivated`, `activating`, `canceled`, `paused`, `activated`, `error`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignmentConfigurations | [deviceAndAppManagementRingAssignmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementringassignmentconfiguration?view=graph-rest-beta) collection | The collection of assignment configurations associated with this deployment ring. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementDeploymentRing",
  "id": "String (identifier)",
  "displayName": "String",
  "order": 1024,
  "activationCriteria": {
    "@odata.type": "microsoft.graph.deviceAndAppManagementRingActivationDateTimeCriteria",
    "startDateTime": "String (timestamp)"
  },
  "state": "String"
}
```
