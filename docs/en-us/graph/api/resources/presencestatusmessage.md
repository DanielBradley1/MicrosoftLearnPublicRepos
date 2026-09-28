<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/presencestatusmessage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# presenceStatusMessage resource type

Namespace: microsoft.graph

Represents a presence status message related to the [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) of a user in Microsoft Teams.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| expiryDateTime | [dateTimeTimeZone](https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0) | Time in which the status message expires.  <br>If not provided, the status message doesn't expire.  <br>  <br>**expiryDateTime.dateTime** shouldn't include time zone.  <br>  <br>**expiryDateTime** isn't available when you request the presence of another user. |
| message | [itemBody](https://learn.microsoft.com/en-us/graph/api/resources/itembody?view=graph-rest-1.0) | Status message item.  <br>  <br>The only supported format currently is `message.contentType = 'text'`. |
| publishedDateTime | DateTimeOffset | Time in which the status message was published.  <br>Read-only.  <br>  <br>**publishedDateTime** isn't available when you request the presence of another user. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "expiryDateTime": {"@odata.type": "#microsoft.graph.dateTimeTimeZone"},
  "message": {"@odata.type": "#microsoft.graph.itemBody"},
  "publishedDateTime": "String"
}
```
