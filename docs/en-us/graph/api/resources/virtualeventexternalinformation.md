<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/virtualeventexternalinformation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-09 -->

# virtualEventExternalInformation resource type

Namespace: microsoft.graph

Represents the external information for a [virtual event](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0).

The **applicationId** and **externalEventId** properties allow external event information to be associated with a [virtual event](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationId | String | Identifier of the application that hosts the **externalEventId**. Read-only. |
| externalEventId | String | The identifier for a **virtualEventExternalInformation** object that associates the virtual event with an event ID in an external application. This association bundles all the information \(both supported and not supported in [virtualEvent](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0)\) into one virtual event object. Optional. If set, the maximum supported length is 256 characters. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.virtualEventExternalInformation",
  "applicationId": "String",
  "externalEventId": "String"
}
```

## Related content

- [Virtual event](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0)
- [Virtual event townhalls](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0)
- [Virtual event webinars](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventwebinar?view=graph-rest-1.0)
