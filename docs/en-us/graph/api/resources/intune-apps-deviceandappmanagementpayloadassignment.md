<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# deviceAndAppManagementPayloadAssignment resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Polymorphic base type for device and app management assignment containing assignment identifier, assignment source identification details, assignment target and assignment details.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceAndAppManagementPayloadAssignments](https://learn.microsoft.com/en-us/graph/api/intune-apps-deviceandappmanagementpayloadassignment-list?view=graph-rest-beta) | [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) collection | List properties and relationships of the [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) objects. |
| [Get deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-deviceandappmanagementpayloadassignment-get?view=graph-rest-beta) | [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) | Read properties and relationships of the [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) object. |
| [Create deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-deviceandappmanagementpayloadassignment-create?view=graph-rest-beta) | [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) | Create a new [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) object. |
| [Delete deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-deviceandappmanagementpayloadassignment-delete?view=graph-rest-beta) | None | Deletes a [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta). |
| [Update deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/intune-apps-deviceandappmanagementpayloadassignment-update?view=graph-rest-beta) | [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) | Update the properties of a [deviceAndAppManagementPayloadAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-deviceandappmanagementpayloadassignment?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for this assignment. Returned by default. This property is read-only. |
| payloadId | String | The unique identifier \(Guid\) for the payload associated with this assignment. Returned by default. |
| target | [deviceAndAppManagementAssignmentTarget](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmenttarget?view=graph-rest-beta) | The target group for this assignment. This value will be supplied on write operation only for direct/policy set assignments. This value will not be supplied on write operation for deployment assignments. However, it is populated when reading any assignment. |
| assignmentDetail | [deviceAndAppManagementAssignmentDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceandappmanagementassignmentdetail?view=graph-rest-beta) | Type encapsulating additional properties for an assignment except for assignment target \(group, assignment filter, identifier information\). |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementPayloadAssignment",
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
  }
}
```
