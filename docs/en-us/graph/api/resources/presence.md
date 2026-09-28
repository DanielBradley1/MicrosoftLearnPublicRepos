<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-19 -->

# presence resource type

Namespace: microsoft.graph

Contains information about a user's presence, including their availability and user activity.

This resource supports subscribing to [change notifications](https://learn.microsoft.com/en-us/graph/changenotifications-for-presence).

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get presence](https://learn.microsoft.com/en-us/graph/api/presence-get?view=graph-rest-1.0) | [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) | Get a user's presence information. |
| [Get presence for multiple users](https://learn.microsoft.com/en-us/graph/api/cloudcommunications-getpresencesbyuserid?view=graph-rest-1.0) | [presence](https://learn.microsoft.com/en-us/graph/api/resources/presence?view=graph-rest-1.0) collection | Get the presence information for multiple users. |
| [Set presence](https://learn.microsoft.com/en-us/graph/api/presence-setpresence?view=graph-rest-1.0) |  | Set an application's presence session for a user. |
| [Clear presence](https://learn.microsoft.com/en-us/graph/api/presence-clearpresence?view=graph-rest-1.0) |  | Clear an application's presence session for a user. |
| [Set user preferred presence](https://learn.microsoft.com/en-us/graph/api/presence-setuserpreferredpresence?view=graph-rest-1.0) |  | Set the preferred availability and activity status for a user. |
| [Clear user preferred presence](https://learn.microsoft.com/en-us/graph/api/presence-clearuserpreferredpresence?view=graph-rest-1.0) |  | Clear the preferred availability and activity status for a user. |
| [Set user status message](https://learn.microsoft.com/en-us/graph/api/presence-setstatusmessage?view=graph-rest-1.0) |  | Set a presence status message for a user. |
| [Set automatic location](https://learn.microsoft.com/en-us/graph/api/presence-setautomaticlocation?view=graph-rest-1.0) | None | Update the automatic work location for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| [Set manual location](https://learn.microsoft.com/en-us/graph/api/presence-setmanuallocation?view=graph-rest-1.0) | None | Set the manual work location signal for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| [Clear automatic location](https://learn.microsoft.com/en-us/graph/api/presence-clearautomaticlocation?view=graph-rest-1.0) | None | Clear the automatic work location signal for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0). |
| [Clear location](https://learn.microsoft.com/en-us/graph/api/presence-clearlocation?view=graph-rest-1.0) | None | Clear the work location signals for a [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0), including both the manual and automatic layers for the current date. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| activity | String | The supplemental information to a user's availability. Possible values are `available`, `away`, `beRightBack`, `busy`, `doNotDisturb`, `offline`, `outOfOffice`, `presenceUnknown`. |
| availability | String | The base presence information for a user. Possible values are `available`, `away`, `beRightBack`, `busy`, `doNotDisturb`, `focusing`, `inACall`, `inAMeeting`, `offline`, `presenting`, `presenceUnknown`. |
| id | String | The unique identifier for the user. |
| outOfOfficeSettings | [outOfOfficeSettings](https://learn.microsoft.com/en-us/graph/api/resources/outofofficesettings?view=graph-rest-1.0) | The out of office settings for a user. |
| sequenceNumber | String | The lexicographically sortable String stamp that represents the version of a **presence** object. |
| statusMessage | [presenceStatusMessage](https://learn.microsoft.com/en-us/graph/api/resources/presencestatusmessage?view=graph-rest-1.0) | The presence status message of a user. |
| workLocation | [userWorkLocation](https://learn.microsoft.com/en-us/graph/api/resources/userworklocation?view=graph-rest-1.0) | Represents the user’s aggregated work location state. |

Note

- To learn more about the different presence states, see [User presence in Teams](https://learn.microsoft.com/en-us/microsoftteams/presence-admins).
- For more details about presence sessions, states permutations, timeouts, and trusted domains, see [Manage presence state using the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/cloud-communications-manage-presence-state).

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
   "activity": "String",
   "availability":"String",
   "id": "String (identifier)",
   "outOfOfficeSettings": {"@odata.type": "#microsoft.graph.outOfOfficeSettings"},
   "sequenceNumber": "String",
   "statusMessage": {"@odata.type": "#microsoft.graph.presenceStatusMessage"},
   "workLocation": {"@odata.type": "microsoft.graph.userWorkLocation" }
}
```
