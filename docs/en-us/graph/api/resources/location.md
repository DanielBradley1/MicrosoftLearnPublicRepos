<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/location?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# Location resource type

Namespace: microsoft.graph

Represents location information of an [event](https://learn.microsoft.com/en-us/graph/api/resources/event?view=graph-rest-1.0).

There are multiple ways to create events in a calendar, for example, through an app using the [create event](https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0) REST API, or manually using the Outlook user interface. When you create an event using the user interface, you can specify the location as plain text \(for example, "Harry's Bar"\), or from the rooms list provided by Outlook, Bing Autosuggest, or Bing local search.

Depending on how an event is created, expect Outlook to set the read-only **locationType** property differently.

| How event was created | Property | Expected value |
| :--- | :--- | :--- |
| [create event](https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0) REST API | **locationType** | `default` |
| User interface in Outlook | **locationType** | One of the following:<br><br>- `default` for a location entered as plain text.<br>- `conferenceRoom` for a room provided by the Outlook rooms list.<br>- Or, any of this list - `homeAddress`, `businessAddress`,`geoCoordinates`, `streetAddress`, `hotel`, `restaurant`, `localBusiness`, `postalAddress` - for a location from Bing Autosuggest or Bing local search. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| address | [physicalAddress](https://learn.microsoft.com/en-us/graph/api/resources/physicaladdress?view=graph-rest-1.0) | The street address of the location. |
| coordinates | [outlookGeoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/outlookgeocoordinates?view=graph-rest-1.0) | The geographic coordinates and elevation of the location. |
| displayName | String | The name associated with the location. |
| locationEmailAddress | String | Optional email address of the location. |
| locationUri | String | Optional URI representing the location. |
| locationType | locationType | The type of location. The possible values are: `default`, `conferenceRoom`, `homeAddress`, `businessAddress`,`geoCoordinates`, `streetAddress`, `hotel`, `restaurant`, `localBusiness`, `postalAddress`. Read-only. |
| uniqueId | String | For internal use only. |
| uniqueIdType | locationUniqueIdType | For internal use only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "address": {"@odata.type": "microsoft.graph.physicalAddress"},
  "coordinates": {"@odata.type": "microsoft.graph.outlookGeoCoordinates"},
  "displayName": "string",
  "locationEmailAddress": "string",
  "locationUri": "string",
  "locationType": "string",
  "uniqueId": "string",
  "uniqueIdType": "string"
}
```
