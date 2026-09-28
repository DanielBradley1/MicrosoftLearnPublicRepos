<!-- Source: https://learn.microsoft.com/en-us/graph/api/openshift-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-26 -->

# Update openShift

Namespace: microsoft.graph

Update the properties of an [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) object.

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
PUT /teams/{id}/schedule/openShifts/{openShiftId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-type | application/json. Required. |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| draftOpenShift | [openShiftItem](https://learn.microsoft.com/en-us/graph/api/resources/openshiftitem?view=graph-rest-1.0) | Draft changes in the **openShift** are only visible to managers until they're [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). Either **draftOpenShift** or **sharedOpenShift** should be `null`. |
| isStagedForDeletion | Boolean | The **openShift** is marked for deletion, a process that is finalized when the schedule is [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0). Optional. |
| schedulingGroupId | String | The ID of the [schedulingGroup](https://learn.microsoft.com/en-us/graph/api/resources/schedulinggroup?view=graph-rest-1.0) that contains the **openShift**. |
| sharedOpenShift | [openShiftItem](https://learn.microsoft.com/en-us/graph/api/resources/openshiftitem?view=graph-rest-1.0) | The shared version of this **openShift** that is viewable by both employees and managers. Either **draftOpenShift** or **sharedOpenShift** should be `null`. |

## Response

If successful, this method returns a `204 No Content` response code and empty content. If the request specifies the `Prefer` header with `return=representation` preference, then this method returns a `200 OK` response code and an updated [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/v1.0/teams/3d88b7a2-f988-4f4b-bb34-d66df66af126/schedule/openShifts/OPNSHFT_577b75d2-a927-48c0-a5d1-dc984894e7b8
Content-Type: application/json

{
  "schedulingGroupId": "TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a",
  "sharedOpenShift": {
    "displayName": null,
    "startDateTime": "2024-11-04T20:00:00Z",
    "endDateTime": "2024-11-04T21:00:00Z",
    "theme": "blue",
    "notes": null,
    "openSlotCount": 1,
    "activities": []
  },
  "draftTimeOff": null,
  "isStagedForDeletion": false
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const openShift = {
  schedulingGroupId: 'TAG_4ab7d329-1f7e-4eaf-ba93-63f1ff3f3c4a',
  sharedOpenShift: {
    displayName: null,
    startDateTime: '2024-11-04T20:00:00Z',
    endDateTime: '2024-11-04T21:00:00Z',
    theme: 'blue',
    notes: null,
    openSlotCount: 1,
    activities: []
  },
  draftTimeOff: null,
  isStagedForDeletion: false
};

await client.api('/teams/3d88b7a2-f988-4f4b-bb34-d66df66af126/schedule/openShifts/OPNSHFT_577b75d2-a927-48c0-a5d1-dc984894e7b8')
	.put(openShift);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
