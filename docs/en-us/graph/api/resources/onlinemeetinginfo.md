<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onlinemeetinginfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# onlineMeetingInfo resource type

Details for an attendee to join the meeting online.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conferenceId | String | The ID of the conference. |
| joinUrl | String | The external link that launches the online meeting. This is a URL that clients launch into a browser and will redirect the user to join the meeting. |
| phones | [phone](https://learn.microsoft.com/en-us/graph/api/resources/phone?view=graph-rest-1.0) collection | All of the phone numbers associated with this conference. |
| quickDial | String | The preformatted quick dial for this call. |
| tollFreeNumbers | String collection | The toll free numbers that can be used to join the conference. |
| tollNumber | String | The toll number that can be used to join the conference. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "conferenceId": "String",
  "joinUrl": "String",
  "phones": [{"@odata.type": "microsoft.graph.phone"}],
  "quickDial": "String",
  "tollFreeNumbers": ["String"],
  "tollNumber": "String"
}
```
