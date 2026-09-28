<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementIntentUserState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity that represents user state for an intent

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementIntentUserStates](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentuserstate-list?view=graph-rest-beta) | [deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate?view=graph-rest-beta) objects. |
| [Get deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentuserstate-get?view=graph-rest-beta) | [deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate?view=graph-rest-beta) object. |
| [Create deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentuserstate-create?view=graph-rest-beta) | [deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate?view=graph-rest-beta) | Create a new [deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate?view=graph-rest-beta) object. |
| [Delete deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentuserstate-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate?view=graph-rest-beta). |
| [Update deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementintentuserstate-update?view=graph-rest-beta) | [deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate?view=graph-rest-beta) | Update the properties of a [deviceManagementIntentUserState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementintentuserstate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The ID |
| userPrincipalName | String | The user principal name that is being reported on a device |
| userName | String | The user name that is being reported on a device |
| deviceCount | Int32 | Count of Devices that belongs to a user for an intent |
| lastReportedDateTime | DateTimeOffset | Last modified date time of an intent report |
| state | [complianceStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-compliancestatus?view=graph-rest-beta) | User state for an intent. Possible values are: `unknown`, `notApplicable`, `compliant`, `remediated`, `nonCompliant`, `error`, `conflict`, `notAssigned`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementIntentUserState",
  "id": "String (identifier)",
  "userPrincipalName": "String",
  "userName": "String",
  "deviceCount": 1024,
  "lastReportedDateTime": "String (timestamp)",
  "state": "String"
}
```
