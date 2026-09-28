<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bitlocker?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# bitlocker resource type

Namespace: microsoft.graph

The parent resource for a stored BitLocker key with the navigation property **bitlockerRecoveryKey** which contains the actual recovery key.

## Methods

None.

## Properties

None.

## Relationships

| Relationship | Type | Description |
| --- | --- | --- |
| recoveryKeys | [bitlockerRecoveryKey](https://learn.microsoft.com/en-us/graph/api/resources/bitlockerrecoverykey?view=graph-rest-1.0) collection | The recovery keys associated with the bitlocker entity. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bitlocker"
}
```
