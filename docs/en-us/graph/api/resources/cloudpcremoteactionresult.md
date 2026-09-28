<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcremoteactionresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-06-10 -->

# cloudPcRemoteActionResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a remote action result specified by a Cloud PC.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Retrieve remote action results](https://learn.microsoft.com/en-us/graph/api/cloudpc-retrievecloudpcremoteactionresults?view=graph-rest-beta) | [cloudPcRemoteActionResult](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcremoteactionresult?view=graph-rest-beta) collection | Retrieve [remote action results](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcremoteactionresult?view=graph-rest-beta) and check the status of a specific remote action performed on the associated Cloud PC device. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| actionName | String | The specified action. Supported values in the Microsoft Endpoint Manager portal are: `Reprovision`, `Resize`, `Restore`. Supported values in enterprise Cloud PC devices are: `Reboot`, `Rename`, `Reprovision`, `Troubleshoot`. |
| actionState | [actionState](#actionstate-values) | State of the action. The possible values are: `None`, `pending`, `canceled`, `active`, `done`, `failed`, `notSupported`. Read-only. |
| cloudPcId | String | The ID of the Cloud PC device on which the remote action is performed. Read-only. |
| managedDeviceId | String | The ID of the Intune managed device on which the remote action is performed. Read-only. |
| startDateTime | DateTimeOffset | Time the action was initiated. The Timestamp is shown in ISO 8601 format and Coordinated Universal Time \(UTC\). For example, midnight UTC on Jan 1, 2014 appears as '2014-01-01T00:00:00Z'. |
| lastUpdatedDateTime | DateTimeOffset | Last update time for action. The Timestamp is shown in ISO 8601 format and Coordinated Universal Time \(UTC\). For example, midnight UTC on Jan 1, 2014 appears as '2014-01-01T00:00:00Z'. |
| statusDetail | [cloudPcStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcstatusdetail?view=graph-rest-beta) | The extended details of the action status, including error code, error message, and additional information. For example, `"statusDetail": {"code": "internalServerError","message": "There was an internal server error. Please contact support xxx.","additionalInformation": [ { "@odata.type":"microsoft.graph.keyValuePair","name": "correlationId","value": "52367774-cfb7-4e9c-ab51-1b864c31f2d1"} ]}` |
| statusDetails \(deprecated\) | [cloudPcStatusDetails](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcstatusdetails?view=graph-rest-beta) | The details of the Cloud PC status. This property is deprecated and will no longer be supported effective August 31, 2024. Use statusDetail instead. |

### actionState values

| Member | Description |
| :--- | :--- |
| none | Not a valid action state. |
| pending | The action is pending. |
| canceled | The action is canceled. |
| active | The action is active. |
| done | The action completed without errors. |
| failed | The action failed. |
| notSupported | The action isn't supported. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcRemoteActionResult",
  "actionName": "String",
  "actionState": "String",
  "startDateTime": "String (timestamp)",
  "lastUpdatedDateTime": "String (timestamp)",
  "cloudPcId": "String",
  "managedDeviceId": "String",
  "statusDetails": {
    "@odata.type": "microsoft.graph.cloudPcStatusDetails"
  },
  "statusDetail": {
    "@odata.type": "microsoft.graph.cloudPcStatusDetail"
  }
}
```
