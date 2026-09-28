<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/meetingcapability?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# meetingCapability resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the capabilities of a meeting

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowAnonymousUsersToDialOut | Boolean | Indicates whether anonymous users dialout is allowed in a meeting. |
| allowAnonymousUsersToStartMeeting | Boolean | Indicates whether anonymous users are allowed to start a meeting. |
| autoAdmittedUsers | autoAdmittedUsersType | The possible values are: `everyoneInCompany`, `everyone`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "allowAnonymousUsersToDialOut": true,
  "allowAnonymousUsersToStartMeeting": true,
  "autoAdmittedUsers": "everyoneInCompany | everyone"
}
```
