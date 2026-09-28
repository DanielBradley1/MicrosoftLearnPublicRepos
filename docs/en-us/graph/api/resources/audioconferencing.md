<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/audioconferencing?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# audioConferencing resource type

Namespace: microsoft.graph

Represents phone access information for an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conferenceId | String | The conference id of the online meeting. |
| dialinUrl | String | A URL to the externally-accessible web page that contains dial-in information. |
| tollFreeNumbers | String collection | List of toll-free numbers that are displayed in the meeting invite. |
| tollNumbers | String collection | List of toll numbers that are displayed in the meeting invite. |
| tollFreeNumber \(deprecated\) | String | The toll-free number that connects to the Audio Conference Provider. |
| tollNumber \(deprecated\) | String | The toll number that connects to the Audio Conference Provider. |

Caution

- The **tollFreeNumber** and **tollNumber** properties are deprecated. Use the **tollFreeNumbers** and **tollNumbers** properties instead.
- For backward compatibility, the original **tollFreeNumber** is added to the new **tollFreeNumbers** collection and the original **tollNumber** is added to the new **tollNumbers** collection.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "conferenceId": "String",
  "dialinUrl": "String",
  "tollFreeNumbers": [ "String" ],
  "tollNumbers": [ "String" ]
}
```
