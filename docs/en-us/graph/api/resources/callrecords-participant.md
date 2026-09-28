<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-04-16 -->

# participant resource type

Namespace: microsoft.graph.callRecords

Represents the identity of a participant in a [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0).

Inherits from [participantBase](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participantbase?view=graph-rest-1.0).

Note

A known issue related to application identities is associated with this API. For details, see [Known issues](https://developer.microsoft.com/graph/known-issues?search=25794).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/callrecords-callrecord-list-participants_v2?view=graph-rest-1.0) | [microsoft.graph.callRecords.participant](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant?view=graph-rest-1.0) collection | Get the list of [participant](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participant?view=graph-rest-1.0) objects associated with a [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the call participant. Inherited from [participantBase](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participantbase?view=graph-rest-1.0). |
| identity | [microsoft.graph.communicationsIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/communicationsidentityset?view=graph-rest-1.0) | The identity of the call participant. Inherited from [participantBase](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participantbase?view=graph-rest-1.0). |
| administrativeUnitInfos | [microsoft.graph.callRecords.administrativeUnitInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-administrativeunitinfo?view=graph-rest-1.0) collection | List of [administrativeUnitInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-administrativeunitinfo?view=graph-rest-1.0) objects for the call participant. Inherited from [participantBase](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participantbase?view=graph-rest-1.0). |

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

For examples that show how to use the **participant** resource, see [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0).
