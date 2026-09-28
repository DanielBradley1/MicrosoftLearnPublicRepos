<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-03 -->

# teamworkDeviceOperation resource type

Namespace: microsoft.graph

Note

The Microsoft Graph beta APIs related to device management under the `teamworkDevice` resource type will be deprecated by November 2025 and will no longer be supported after that date.

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents details about async operations running on a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta), including operation status. Any async operation running on a device creates a **teamworkDeviceOperation** object.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/teamworkdeviceoperation-list?view=graph-rest-beta) | [teamworkDeviceOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceoperation?view=graph-rest-beta) collection | Get a list of the [teamworkDeviceOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceoperation?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamworkdeviceoperation-get?view=graph-rest-beta) | [teamworkDeviceOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceoperation?view=graph-rest-beta) | Read the properties and relationships of a [teamworkDeviceOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceoperation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completedDateTime | DateTimeOffset | Time at which the operation reached a final state \(for example, `Successful`, `Failed`, and `Cancelled`\). |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who created the device operation. |
| createdDateTime | DateTimeOffset | The UTC date and time when the device operation was created. |
| error | [operationError](https://learn.microsoft.com/en-us/graph/api/resources/operationerror?view=graph-rest-beta) | Error details are available only in case of a failed status. |
| id | String | Document identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastActionBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who last modified the device operation. |
| lastActionDateTime | DateTimeOffset | The UTC date and time when the device operation was last modified. |
| operationType | teamworkDeviceOperationType | Type of async operation on a device. The possible values are: `deviceRestart`, `configUpdate`, `deviceDiagnostics`, `softwareUpdate`, `deviceManagementAgentConfigUpdate`, `remoteLogin`, `remoteLogout`, `unknownFutureValue`. |
| startedDateTime | DateTimeOffset | Time at which the operation was started. |
| status | String | The current status of the async operation, for example, `Queued`, `Scheduled`, `InProgress`, `Successful`, `Cancelled`, and `Failed`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkDeviceOperation",
  "completedDateTime": "String (timestamp)",
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "error": {
    "@odata.type": "microsoft.graph.operationError"
  },
  "id": "String (identifier)",
  "lastActionBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastActionDateTime": "String (timestamp)",
  "operationType": "String",
  "startedDateTime": "String (timestamp)",
  "status": "String"
}
```
