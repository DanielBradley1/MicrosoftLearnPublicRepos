<!-- Source: https://learn.microsoft.com/en-us/graph/api/timeoff-put?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-26 -->

# Replace timeOff

Namespace: microsoft.graph

Replace an existing [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) object.

If the specified [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) object doesn't exist, this method returns `404 Not found`.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group.Read.All | Schedule.ReadWrite.All, Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

> **Note**: This API supports admin permissions. Users with admin roles can access groups that they are not a member of.

## HTTP request

```http
PUT /teams/{teamId}/schedule/timesOff/{timeOffId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| draftTimeOff | [timeOffItem](https://learn.microsoft.com/en-us/graph/api/resources/timeoffitem?view=graph-rest-1.0) | The draft version of this **timeOff** item that is viewable by managers. It must be shared before it is visible to team members. Either **draftOpenShift** or **sharedOpenShift** should be `null`. |
| isStagedForDeletion | Boolean | The **timeOff** is marked for deletion, a process that is finalized when the schedule is [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). Optional |
| sharedTimeOff | [timeOffItem](https://learn.microsoft.com/en-us/graph/api/resources/timeoffitem?view=graph-rest-1.0) | The shared version of this **timeOff** that is viewable by both employees and managers. Updates to the **sharedTimeOff** property send notifications to users in the Teams client. Either **draftOpenShift** or **sharedOpenShift** should be `null`. |
| userId | String | ID of the user assigned to the **timeOff**. Required. |

## Response

If successful, this method returns a `204 No Content` response code and empty content. If the request specifies the `Prefer` header with `return=representation` preference, then this method returns a `200 OK` response code and a [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) object in the response body.

## Example

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/teams/{teamId}/schedule/timesOff/{timeOffId}
Content-type: application/json

{
  "userId": "aa162a04-bec6-4b81-ba99-96caa7b2b24d",
  "sharedTimeOff": {
    "timeOffReasonId": "TOR_29a5ba96-c7ef-4e76-bec6-055323746314",
    "startDateTime": "2024-10-10T19:00:00Z",
    "endDateTime": "2024-10-10T20:00:00Z",
    "theme": "blue"
  },
  "draftTimeOff": null
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const timeOff = {
  userId: 'aa162a04-bec6-4b81-ba99-96caa7b2b24d',
  sharedTimeOff: {
    timeOffReasonId: 'TOR_29a5ba96-c7ef-4e76-bec6-055323746314',
    startDateTime: '2024-10-10T19:00:00Z',
    endDateTime: '2024-10-10T20:00:00Z',
    theme: 'blue'
  },
  draftTimeOff: null
};

await client.api('/teams/{teamId}/schedule/timesOff/{timeOffId}')
	.put(timeOff);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
