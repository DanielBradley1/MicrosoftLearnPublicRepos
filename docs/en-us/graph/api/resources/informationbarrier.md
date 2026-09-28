<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/informationbarrier?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-18 -->

# informationBarrier resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the information barrier of a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-beta) object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mode | [informationBarrierMode](#informationbarriermode-values) | Indicates the information barrier mode. The possible values are: `open`, `ownerModerated`, `explicit`, and `unknownFutureValue`. |
| segmentIds | `Collection(Guid)` | The list of segment IDs associated with the container. |

### informationBarrierMode values

| Member | Description |
| :--- | :--- |
| open | A container has no segments and collaboration is unrestricted. |
| ownerModerated | Owner moderates the collaboration between incompatible segments. |
| explicit | Collaboration between incompatible segments is explicitly restricted. |
| unknownFutureValue | Unknown future value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.informationBarrier",
  "mode": "String",
  "segmentIds": [ "Guid" ]
}
```
