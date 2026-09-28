<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceactivity?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-03 -->

# teamworkDeviceActivity resource type

Namespace: microsoft.graph

Note

The Microsoft Graph beta APIs related to device management under the `teamworkDevice` resource type will be deprecated by November 2025 and will no longer be supported after that date.

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents activity details for a Microsoft Teams-enabled [device](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdevice?view=graph-rest-beta), including the active peripheral devices attached to the device.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/teamworkdeviceactivity-get?view=graph-rest-beta) | [teamworkDeviceActivity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceactivity?view=graph-rest-beta) | Read the properties and relationships of a [teamworkDeviceActivity](https://learn.microsoft.com/en-us/graph/api/resources/teamworkdeviceactivity?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activePeripherals | [teamworkActivePeripherals](https://learn.microsoft.com/en-us/graph/api/resources/teamworkactiveperipherals?view=graph-rest-beta) | The active peripheral devices attached to the device. |
| createdBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who created the device activity document. |
| createdDateTime | DateTimeOffset | The UTC date and time when the device activity document was created. |
| id | String | Document identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedBy | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta) | Identity of the user who last modified the device activity details. |
| lastModifiedDateTime | DateTimeOffset | The UTC date and time when the device activity detail was last modified. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.teamworkDeviceActivity",
  "activePeripherals": {
    "@odata.type": "microsoft.graph.teamworkActivePeripherals"
  },
  "createdBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "createdDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.identitySet"
  },
  "lastModifiedDateTime": "String (timestamp)"
}
```
