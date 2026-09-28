<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participantbase?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-11-12 -->

# participantBase resource type

Namespace: microsoft.graph.callRecords

Represents the base identity of a participant or organizer in a [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0).

Base type of [organizer](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-organizer?view=graph-rest-1.0) and [participant](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the call participant. |
| identity | [microsoft.graph.communicationsIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/communicationsidentityset?view=graph-rest-1.0) | The identity of the call participant. |
| administrativeUnitInfos | [microsoft.graph.callRecords.administrativeUnitInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-administrativeunitinfo?view=graph-rest-1.0) collection | List of [administrativeUnitInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-administrativeunitinfo?view=graph-rest-1.0) objects for the call participant. |

## Methods

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "identity": {"@odata.type": "microsoft.graph.communicationsIdentitySet"},
  "administrativeUnitInfos": [{"@odata.type": "microsoft.graph.callRecords.administrativeUnitInfo"}]
}
```

## See also

For examples that show how to use the **participant** and **organizer** resources, see [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0).
