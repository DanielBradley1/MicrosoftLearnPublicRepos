<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/outofofficesettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-12 -->

# outOfOfficeSettings resource type

Namespace: microsoft.graph

Represents the out-of-office settings related to the [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) of a user.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isOutOfOffice | Boolean | If `true`, either of the following is met:  <br><br><br>- The current time falls within the out-of-office window configured in Outlook or Teams.<br>- An event marked as "Show as Out of Office" appears on the user's calendar.<br><br>Otherwise, false. |
| message | String | The out-of-office message configured by the user in the Outlook client \(Automatic replies\) or the Teams client \(Schedule out of office\). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isOutOfOffice": "Boolean",
  "message": "String"
}
```
