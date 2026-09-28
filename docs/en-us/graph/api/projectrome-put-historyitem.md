<!-- Source: https://learn.microsoft.com/en-us/graph/api/projectrome-put-historyitem?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-22 -->

# Create or replace an activityHistoryItem

Namespace: microsoft.graph

Create a new or replace an existing history item for an existing user activity.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | UserActivity.ReadWrite.CreatedByApp | Not available. |
| Delegated \(personal Microsoft account\) | UserActivity.ReadWrite.CreatedByApp | Not available. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PUT /me/activities/{id}/historyItems/{id}
```

`{id}` needs to be a GUID.

## Request headers

| Name | Type | Description |
| :--- | :--- | :--- |
| Authorization | string | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of an [activityHistoryItem](https://learn.microsoft.com/en-us/graph/api/resources/projectrome-historyitem?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code if the **activityHistoryItem** was created or `200 OK` if the **activityHistoryItem** was replaced.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/me/activities/{activity-id}/historyItems/{item-id}
Content-type: application/json

{
    "startedDateTime": "2015-02-11T20:54:04.3457274+00:00",
    "userTimezone": "Africa/Casablanca",
    "lastActiveDateTime": "2015-02-11T20:54:04.3457274+00:00"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const activityHistoryItem = {
    startedDateTime: '2015-02-11T20:54:04.3457274+00:00',
    userTimezone: 'Africa/Casablanca',
    lastActiveDateTime: '2015-02-11T20:54:04.3457274+00:00'
};

await client.api('/me/activities/{activity-id}/historyItems/{item-id}')
	.put(activityHistoryItem);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('user%40contoso.com')/activities('13881113971988980728')/historyItems/$entity",
    "status": "updated",
    "userTimezone": "Africa/Casablanca",
    "createdDateTime": "2018-02-26T20:28:22.14Z",
    "lastModifiedDateTime": "2018-02-26T20:28:22.155Z",
    "id": "9d0b74e4-4b41-43ea-b34d-f9c1bf9f809c",
    "startedDateTime": "2018-02-26T20:54:04.345Z",
    "lastActiveDateTime": "2018-02-26T20:54:24.345Z",
    "expirationDateTime": "2018-03-28T20:28:22.14Z",
    "activeDurationSeconds": 20
}
```
