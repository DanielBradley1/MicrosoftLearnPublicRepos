<!-- Source: https://learn.microsoft.com/en-us/graph/api/shift-put?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-26 -->

# Replace shift

Namespace: microsoft.graph

Replace an existing [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0).

If the specified [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) doesn't exist, this method returns `404 Not found`.

The duration of a shift can't be less than one minute or longer than 24 hours.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

## HTTP request

```http
PUT /teams/{teamId}/schedule/shifts/{shiftId}
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
| draftShift | [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0) | Draft changes in the **shift**. Draft changes are only visible to managers. The changes are visible to employees when they're [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0), which copies the changes from the **draftShift** to the **sharedShift** property. Either **draftOpenShift** or **sharedOpenShift** should be `null`. |
| isStagedForDeletion | Boolean | The **shift** is marked for deletion, a process that is finalized when the schedule is [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). Optional. |
| schedulingGroupId | String | ID of the scheduling group the **shift** is part of. Required. |
| sharedShift | [shiftItem](https://learn.microsoft.com/en-us/graph/api/resources/shiftitem?view=graph-rest-1.0) | The shared version of this **shift** that is viewable by both employees and managers. Updates to the **sharedShift** property send notifications to users in the Teams client. Either **draftOpenShift** or **sharedOpenShift** should be `null`. |
| userId | String | ID of the user assigned to the **shift**. Required. |

## Response

If successful, this method returns a `204 No Content` response code and empty content. If the request specifies the `Prefer` header with `return=representation` preference, then this method returns a `200 OK` response code and a [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0) object in the response body.

## Example

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/teams/{teamId}/schedule/shifts/{shiftId}
Content-type: application/json

{
  "userId": "5ca83ce7-291d-43b7-bf53-af79eef4bc1d",
  "draftShift": {
    "displayName": null,
    "startDateTime": "2024-10-08T15:00:00Z",
    "endDateTime": "2024-10-09T00:00:00Z",
    "theme": "blue",
    "notes": null,
    "activities": []
  },
  "sharedShift": null,
  "isStagedForDeletion": false
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const shift = {
  userId: '5ca83ce7-291d-43b7-bf53-af79eef4bc1d',
  draftShift: {
    displayName: null,
    startDateTime: '2024-10-08T15:00:00Z',
    endDateTime: '2024-10-09T00:00:00Z',
    theme: 'blue',
    notes: null,
    activities: []
  },
  sharedShift: null,
  isStagedForDeletion: false
};

await client.api('/teams/{teamId}/schedule/shifts/{shiftId}')
	.put(shift);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 204 No Content
```
