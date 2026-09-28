<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-organizer?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# organizer resource type

Namespace: microsoft.graph.callRecords

Represents the identity of a call or meeting organizer in a [callRecord](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0).

Inherits from [participantBase](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participantbase?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the call organizer. Inherited from [participantBase](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participantbase?view=graph-rest-1.0). |
| identity | [microsoft.graph.communicationsIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/communicationsidentityset?view=graph-rest-1.0) | The identity of the call organizer. Inherited from [participantBase](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participantbase?view=graph-rest-1.0). |
| administrativeUnitInfos | [microsoft.graph.callRecords.administrativeUnitInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-administrativeunitinfo?view=graph-rest-1.0) collection | The list of [administrativeUnitInfo](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-administrativeunitinfo?view=graph-rest-1.0) objects for the call participant. Inherited from [participantBase](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-participantbase?view=graph-rest-1.0). |

## Methods

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identity)",
  "identity": {"@odata.type": "microsoft.graph.communicationsIdentitySet"},
  "administrativeUnitInfos": [{"@odata.type": "microsoft.graph.callRecords.administrativeUnitInfo"}]
}
```

## See also

For examples that show how to use the **organizer** resource, see [callRecord resource type](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-callrecord?view=graph-rest-1.0).
