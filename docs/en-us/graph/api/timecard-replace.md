<!-- Source: https://learn.microsoft.com/en-us/graph/api/timecard-replace?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-26 -->

# Replace timeCard

Namespace: microsoft.graph

Replace an existing [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

## HTTP request

```http
PUT /teams/{teamsId}/schedule/timeCards/{timeCardId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, supply a JSON representation of a [timeCard](https://learn.microsoft.com/en-us/graph/api/resources/timecard?view=graph-rest-1.0).

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/teams/871dbd5c-3a6a-4392-bfe1-042452793a50/schedule/timeCards/TCK_29ad0a09-b97a-49a2-9490-141cb7602540
Content-type: application/json

{
  "userId": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
  "state": "clockedOut",
  "notes": {
    "contentType": "text",
    "content": "Modified clockOut time"
  },
  "lastModifiedBy": {
    "application": null,
    "device": null,
    "user": {
      "id": "d56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2",
      "displayName": "Alice Bradford"
    }
  },
  "clockInEvent": {
    "dateTime": "2025-01-07T21:00:00Z",
    "isAtApprovedLocation": true,
    "notes": {
      "contentType": "text",
      "content": "Started late due to traffic in CA 237"
    }
  },
  "clockOutEvent": {
    "dateTime": "2025-01-07T21:35:00Z",
    "isAtApprovedLocation": true,
    "notes": null
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const timeCard = {
  userId: 'd56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2',
  state: 'clockedOut',
  notes: {
    contentType: 'text',
    content: 'Modified clockOut time'
  },
  lastModifiedBy: {
    application: null,
    device: null,
    user: {
      id: 'd56f3e8a-2b0f-42b1-88b9-e2dbd12a34d2',
      displayName: 'Alice Bradford'
    }
  },
  clockInEvent: {
    dateTime: '2025-01-07T21:00:00Z',
    isAtApprovedLocation: true,
    notes: {
      contentType: 'text',
      content: 'Started late due to traffic in CA 237'
    }
  },
  clockOutEvent: {
    dateTime: '2025-01-07T21:35:00Z',
    isAtApprovedLocation: true,
    notes: null
  }
};

await client.api('/teams/871dbd5c-3a6a-4392-bfe1-042452793a50/schedule/timeCards/TCK_29ad0a09-b97a-49a2-9490-141cb7602540')
	.put(timeCard);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
