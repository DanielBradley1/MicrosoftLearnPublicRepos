<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementdeploymentassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# deviceAndAppManagementDeploymentAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents a device and app management deployment assignment.

Inherits from [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceAndAppManagementDeploymentAssignments](https://learn.microsoft.com/en-us/graph/api/intune-apps-deviceandappmanagementdeploymentassignment-list?view=graph-rest-beta) | [deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementdeploymentassignment?view=graph-rest-beta) collection | List properties and relationships of the [deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementdeploymentassignment?view=graph-rest-beta) objects. |
| [Get deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-deviceandappmanagementdeploymentassignment-get?view=graph-rest-beta) | [deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementdeploymentassignment?view=graph-rest-beta) | Read properties and relationships of the [deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementdeploymentassignment?view=graph-rest-beta) object. |
| [Create deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-deviceandappmanagementdeploymentassignment-create?view=graph-rest-beta) | [deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementdeploymentassignment?view=graph-rest-beta) | Create a new [deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementdeploymentassignment?view=graph-rest-beta) object. |
| [Delete deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-deviceandappmanagementdeploymentassignment-delete?view=graph-rest-beta) | None | Deletes a [deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementdeploymentassignment?view=graph-rest-beta). |
| [Update deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-deviceandappmanagementdeploymentassignment-update?view=graph-rest-beta) | [deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementdeploymentassignment?view=graph-rest-beta) | Update the properties of a [deviceAndAppManagementDeploymentAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementdeploymentassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for this assignment. Returned by default. This property is read-only. Inherited from [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) |
| payloadId | String | The unique identifier \(Guid\) for the payload associated with this assignment. Returned by default. Inherited from [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The target group for this assignment. This value will be supplied on write operation only for direct/policy set assignments. This value will not be supplied on write operation for deployment assignments. However, it is populated when reading any assignment. Inherited from [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) |
| assignmentDetail | [deviceAndAppManagementAssignmentDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmentdetail?view=graph-rest-beta) | Type encapsulating additional properties for an assignment except for assignment target \(group, assignment filter, identifier information\). Inherited from [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) |
| referenceAssignmentId | String | The unique identifier \(Guid\) of the reference assignment in the deployment. This identifier is generated by server side on deployment creation for each instance of assignment in a ring and is referenced when configuring deployment payload assignments. Returned by default. |
| deploymentId | String | The unique identifier \(Guid\) of the deployment from which this assignment is sourced. Returned by default. This property is read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementDeploymentAssignment",
  "id": "String (identifier)",
  "payloadId": "String",
  "target": {
    "@odata.type": "microsoft.graph.allLicensedUsersAssignmentTarget",
    "deviceAndAppManagementAssignmentFilterId": "String",
    "deviceAndAppManagementAssignmentFilterType": "String"
  },
  "assignmentDetail": {
    "@odata.type": "microsoft.graph.mobileAppAssignmentDetail",
    "intent": "String",
    "settings": {
      "@odata.type": "microsoft.graph.winGetAppAssignmentSettings",
      "notifications": "String",
      "restartSettings": {
        "@odata.type": "microsoft.graph.winGetAppRestartSettings",
        "gracePeriodInMinutes": 1024,
        "countdownDisplayBeforeRestartInMinutes": 1024,
        "restartNotificationSnoozeDurationInMinutes": 1024
      },
      "installTimeSettings": {
        "@odata.type": "microsoft.graph.winGetAppInstallTimeSettings",
        "useLocalTime": true,
        "deadlineDateTime": "String (timestamp)"
      }
    }
  },
  "referenceAssignmentId": "String",
  "deploymentId": "String"
}
```
