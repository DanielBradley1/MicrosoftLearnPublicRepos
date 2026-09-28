<!-- Source: https://learn.microsoft.com/en-us/graph/api/timeoffreason-put?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-26 -->

# Replace timeOffReason

Namespace: microsoft.graph

Replace an existing [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0).

If the specified [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) doesn't exist, this method returns `404 Not found`.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

> **Note**: This API supports admin permissions. Users with admin roles can access groups that they are not a member of.

## HTTP request

```http
PUT /teams/{teamId}/schedule/timeOffReasons/{timeOffReasonId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, supply a JSON representation of a [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `200 OK` response code and a [timeOffReason](https://learn.microsoft.com/en-us/graph/api/resources/timeoffreason?view=graph-rest-1.0) object in the response body.

## Example

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/teams/{teamId}/schedule/timeOffReasons/{timeOffReasonId}
Content-type: application/json
Prefer: return=representation

{
  "displayName": "Vacation",
  "iconType": "plane",
  "isActive": true,
  "code": "VacationCode"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const timeOffReason = {
  displayName: 'Vacation',
  iconType: 'plane',
  isActive: true,
  code: 'VacationCode'
};

await client.api('/teams/{teamId}/schedule/timeOffReasons/{timeOffReasonId}')
	.put(timeOffReason);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "id": "TOR_891045ca-b5d2-406b-aa06-a3c8921245d7",
  "createdDateTime": "2019-03-12T22:10:38.242Z",
  "lastModifiedDateTime": "2019-03-12T22:10:38.242Z",
  "displayName": "Vacation",
  "iconType": "plane",
  "isActive": true,
  "lastModifiedBy": {
    "application": null,
    "device": null,
    "conversation": null,
    "user": {
      "id": "366c0b19-49b1-41b5-a03f-9f3887bd0ed8",
      "displayName": "Alex Wilbur"
    }
  },
  "code": "VacationCode"
}
```
