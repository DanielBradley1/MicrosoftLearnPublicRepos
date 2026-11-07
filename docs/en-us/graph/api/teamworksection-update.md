<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamworksection-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-04 -->

# Update teamworkSection

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [section](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) in a user's [teamwork](https://learn.microsoft.com/en-us/graph/api/resources/userteamwork?view=graph-rest-beta). For system-defined sections, only the **sortType** property can be updated.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamworkSection.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamworkSection.ReadWrite.All | Teamwork.Migrate.All |

## HTTP request

```http
PATCH /users/{user-id}/teamwork/sections/{teamworkSection-id}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of only the properties to update. The following properties can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayIcon | [sectionDisplayIcon](https://learn.microsoft.com/en-us/graph/api/resources/sectiondisplayicon?view=graph-rest-beta) | The icon displayed for the section. |
| displayName | String | The display name of the section. Maximum length is 50 characters. Display names are case-sensitive and must be unique within a user's sections. The reserved system-defined names \(`RecentChats`, `QuickViews`, `TeamsAndChannels`, `MutedChats`, `MeetingChats`, `EngageCommunities`\) can't be used. |
| isExpanded | Boolean | Indicates whether the section is expanded in the user interface. |
| sortType | sectionSortType | The sort order of items in the section. The possible values are: `mostRecent`, `unreadThenMostRecent`, `nameAlphabetical`, `userDefinedCustomOrder`, `unknownFutureValue`. |

Important

The valid **sortType** values depend on the section type:

- *User-defined sections*: `mostRecent`, `unreadThenMostRecent`, and `userDefinedCustomOrder` are valid. `nameAlphabetical` isn't supported.
- *System-defined sections*: The valid values depend on the specific section. For example, the *Teams* and *Channels* sections support `nameAlphabetical`, but the *RecentChats* and *MutedChats* sections don't. When the property **isHierarchicalViewEnabled** is set to `true`, only `nameAlphabetical` is valid.

## Response

If successful, this method returns a `200 OK` response code and an updated [teamworkSection](https://learn.microsoft.com/en-us/graph/api/resources/teamworksection?view=graph-rest-beta) object in the response body.

The following errors are possible.

| Response code | Message |
| :--- | :--- |
| `400 Bad Request` | At least one property must be provided for update. |
| `400 Bad Request` | The 'displayName' property must not be empty or whitespace, or must not exceed 50 characters. |
| `400 Bad Request` | The property '{propertyName}' is read-only or not updatable. Only **displayName**, **displayIcon**, **isExpanded**, and **sortType** can be updated. |
| `400 Bad Request` | The specified sort type is not valid for this section. For more information, see the [Request body](#request-body) section. |
| `403 Forbidden` | This section is system-generated and can't be modified. Only the **sortType** property can be updated on system-defined sections. |
| `404 Not Found` | The specified section wasn't found. |
| `409 Conflict` | A section with this display name already exists. Returned when the requested **displayName** matches an existing user-defined section or a reserved system-defined section name. The comparison is case-sensitive. |
| `409 Conflict` | The section can't be updated because of a concurrent change. Retry the request. |

## Examples

### Example 1: Update the display name of a section

The following example shows how to update the display name of a **teamworkSection** object.

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890
Content-type: application/json

{
  "displayName": "Important Conversations"
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.teamworkSection",
  "@odata.etag": "\"1742515210\"",
  "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "displayName": "Important Conversations",
  "displayIcon": {
    "iconType": "⭐",
    "displayName": "Star",
    "contentUrl": null,
    "skinTone": null
  },
  "sectionType": "userDefined",
  "sortType": "mostRecent",
  "isExpanded": true,
  "isHierarchicalViewEnabled": false,
  "createdDateTime": "2025-01-15T10:30:00Z",
  "lastModifiedDateTime": "2026-03-08T09:15:00Z"
}
```

### Example 2: Update the sort order of a section

The following example shows how to update the sort order of a **teamworkSection** object.

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/users/10f8c3a6-3e2a-4e8b-9c7d-5a4b6c8d9e0f/teamwork/sections/a1b2c3d4-e5f6-7890-abcd-ef1234567890
Content-type: application/json

{
  "sortType": "unreadThenMostRecent"
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.type": "#microsoft.graph.teamworkSection",
  "@odata.etag": "\"1742515220\"",
  "id": "a1b2c3d4-e5f6-7890-abcd-ef1234567890",
  "displayName": "Important Conversations",
  "displayIcon": {
    "iconType": "⭐",
    "displayName": "Star",
    "contentUrl": null,
    "skinTone": null
  },
  "sectionType": "userDefined",
  "sortType": "unreadThenMostRecent",
  "isExpanded": true,
  "isHierarchicalViewEnabled": false,
  "createdDateTime": "2025-01-15T10:30:00Z",
  "lastModifiedDateTime": "2026-03-08T09:20:00Z"
}
```
