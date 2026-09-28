<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# securityBaselineDeviceState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The security baseline compliance state summary of the security baseline for a device.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List securityBaselineDeviceStates](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinedevicestate-list?view=graph-rest-beta) | [securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate?view=graph-rest-beta) collection | List properties and relationships of the [securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate?view=graph-rest-beta) objects. |
| [Get securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinedevicestate-get?view=graph-rest-beta) | [securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate?view=graph-rest-beta) | Read properties and relationships of the [securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate?view=graph-rest-beta) object. |
| [Create securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinedevicestate-create?view=graph-rest-beta) | [securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate?view=graph-rest-beta) | Create a new [securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate?view=graph-rest-beta) object. |
| [Delete securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinedevicestate-delete?view=graph-rest-beta) | None | Deletes a [securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate?view=graph-rest-beta). |
| [Update securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinedevicestate-update?view=graph-rest-beta) | [securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate?view=graph-rest-beta) | Update the properties of a [securityBaselineDeviceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinedevicestate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the entity |
| managedDeviceId | String | Intune device id |
| deviceDisplayName | String | Display name of the device |
| userPrincipalName | String | User Principal Name |
| state | [securityBaselineComplianceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinecompliancestate?view=graph-rest-beta) | Security baseline compliance state. Possible values are: `unknown`, `secure`, `notApplicable`, `notSecure`, `error`, `conflict`. |
| lastReportedDateTime | DateTimeOffset | Last modified date time of the policy report |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.securityBaselineDeviceState",
  "id": "String (identifier)",
  "managedDeviceId": "String",
  "deviceDisplayName": "String",
  "userPrincipalName": "String",
  "state": "String",
  "lastReportedDateTime": "String (timestamp)"
}
```
