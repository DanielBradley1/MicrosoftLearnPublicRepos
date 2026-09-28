<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bitlockerrecoverykey?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-20 -->

# bitlockerRecoveryKey resource type

Namespace: microsoft.graph

Represents a stored BitLocker key that contains the actual recovery key via the **key** property.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/bitlocker-list-recoverykeys?view=graph-rest-1.0) | [bitlockerRecoveryKey](https://learn.microsoft.com/en-us/graph/api/resources/bitlockerrecoverykey?view=graph-rest-1.0) collection | Get a list of the [bitlockerRecoveryKey](https://learn.microsoft.com/en-us/graph/api/resources/bitlockerrecoverykey?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/bitlockerrecoverykey-get?view=graph-rest-1.0) | [bitlockerRecoveryKey](https://learn.microsoft.com/en-us/graph/api/resources/bitlockerrecoverykey?view=graph-rest-1.0) | Retrieve the properties and relationships of a [bitlockerRecoveryKey](https://learn.microsoft.com/en-us/graph/api/resources/bitlockerrecoverykey?view=graph-rest-1.0) object. Note: The **key** property is not returned by default. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the key was originally backed up to Microsoft Entra ID. Not nullable. |
| deviceId | String | Identifier of the device the BitLocker key is originally backed up from. Supports `$filter` \(`eq`\). |
| id | String | The unique identifier for the BitLocker key. |
| key | String | The BitLocker recovery key. Requires `$select` to retrieve. Not nullable. |
| volumeType | volumeType | Indicates the type of volume the BitLocker key is associated with. The possible values are: `1` \(for `operatingSystemVolume`\), `2` \(for `fixedDataVolume`\), `3` \(for `removableDataVolume`\), and `4` \(for `unknownFutureValue`\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bitlockerRecoveryKey",
  "createdDateTime": "String (timestamp)",
  "deviceId": "String",
  "id": "String (identifier)",
  "key": "String",
  "volumeType": "String"
}
```
