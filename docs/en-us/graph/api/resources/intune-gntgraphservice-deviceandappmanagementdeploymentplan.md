<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# deviceAndAppManagementDeploymentPlan resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents a device and app management deployment plan for staged rollout scenarios.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceAndAppManagementDeploymentPlans](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeploymentplan-list?view=graph-rest-beta) | [deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta) collection | List properties and relationships of the [deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta) objects. |
| [Get deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeploymentplan-get?view=graph-rest-beta) | [deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta) | Read properties and relationships of the [deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta) object. |
| [Create deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeploymentplan-create?view=graph-rest-beta) | [deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta) | Create a new [deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta) object. |
| [Delete deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeploymentplan-delete?view=graph-rest-beta) | None | Deletes a [deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta). |
| [Update deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/intune-gntgraphservice-deviceandappmanagementdeploymentplan-update?view=graph-rest-beta) | [deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta) | Update the properties of a [deviceAndAppManagementDeploymentPlan](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymentplan?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key for the resource. |
| versionNumber | Int32 | Version number of the device and app management deployment plan. |
| displayName | String | The display name of the device and app management deployment plan. |
| description | String | The description of the device and app management deployment plan. |
| roleScopeTagIds | String collection | The role scope tag ids to control device and app management deployment plan visibility. |
| topologyDefinitions | [deviceAndAppManagementDeploymentTopologyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceandappmanagementdeploymenttopologydefinition?view=graph-rest-beta) collection | The topology definitions associated with the device and app management deployment plan. |
| allowedPlatform | [devicePlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-gntgraphservice-deviceplatformtype?view=graph-rest-beta) | The allowed assignment filter platform for the device and app management deployment plan. Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidAOSP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`, `windowsMobileApplicationManagement`. |
| createdDateTime | DateTimeOffset | The date and time of when the plan was created \(UTC\). |
| lastModifiedDateTime | DateTimeOffset | The date and time of when the plan was last modified \(UTC\). |
| topologyCount | Int32 | The number of topologies in the deployment plan. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementDeploymentPlan",
  "id": "String (identifier)",
  "versionNumber": 1024,
  "displayName": "String",
  "description": "String",
  "roleScopeTagIds": [
    "String"
  ],
  "topologyDefinitions": [
    {
      "@odata.type": "microsoft.graph.deviceAndAppManagementDeploymentTopologyDefinition",
      "topologyDisplayName": "String",
      "topologyOrder": 1024,
      "topologyActivationCriteria": {
        "@odata.type": "microsoft.graph.deviceAndAppManagementRingActivationDateTimeCriteria",
        "startDateTime": "String (timestamp)"
      },
      "assignmentConfigurations": [
        {
          "@odata.type": "microsoft.graph.deviceAndAppManagementDeploymentTopologyAssignmentConfiguration",
          "target": {
            "@odata.type": "microsoft.graph.organizationalUnitAssignmentTarget",
            "deviceAndAppManagementAssignmentFilterId": "String",
            "deviceAndAppManagementAssignmentFilterType": "String",
            "organizationalUnitId": "String",
            "assignmentConflictSetting": {
              "@odata.type": "microsoft.graph.organizationalUnitAssignmentConflictSetting",
              "assignmentOverride": "String",
              "versionNumber": 1024
            }
          },
          "operation": "String"
        }
      ]
    }
  ],
  "allowedPlatform": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "topologyCount": 1024
}
```
