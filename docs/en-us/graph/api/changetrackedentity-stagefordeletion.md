<!-- Source: https://learn.microsoft.com/en-us/graph/api/changetrackedentity-stagefordeletion?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-06-26 -->

# changeTrackedEntity: stageForDeletion

Namespace: microsoft.graph

Stage the deletion of an [openShift](https://learn.microsoft.com/en-us/graph/api/resources/openshift?view=graph-rest-1.0), [shift](https://learn.microsoft.com/en-us/graph/api/resources/shift?view=graph-rest-1.0), or [timeOff](https://learn.microsoft.com/en-us/graph/api/resources/timeoff?view=graph-rest-1.0) instance in a [schedule](https://learn.microsoft.com/en-us/graph/api/resources/schedule?view=graph-rest-1.0) in draft mode.

Draft changes are only visible to managers. Team members aren't sent notification for draft changes. The deletion is finalized when the schedule is [shared](https://learn.microsoft.com/en-us/graph/api/schedule-share?view=graph-rest-1.0).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Schedule.ReadWrite.All | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

## HTTP request

For an **openShift**:

```http
POST /teams/{teamsId}/schedule/openShifts/{openShiftId}/stageForDeletion
```

For a **shift**:

```http
POST /teams/{teamsId}/schedule/shifts/{shiftId}/stageForDeletion
```

For a **timeOff**:

```http
POST /teams/{teamsId}/schedule/timesOff/{timeOffId}/stageForDeletion
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| MS-APP-ACTS-AS \(deprecated\) | A user ID \(GUID\). Required only if the authorization token is an application token; otherwise, optional. The `MS-APP-ACTS-AS` header is deprecated and no longer required with application tokens. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Example 1: Stage the deletion of an openShift

The following example shows how to stage the deletion of an **openShift** in a **schedule** in draft mode.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/teams/3d88b7a2-f988-4f4b-bb34-d66df66af126/schedule/openShifts/OPNSHFT_577b75d2-a927-48c0-a5d1-dc984894e7b8/stageForDeletion
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/teams/3d88b7a2-f988-4f4b-bb34-d66df66af126/schedule/openShifts/OPNSHFT_577b75d2-a927-48c0-a5d1-dc984894e7b8/stageForDeletion')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Stage the deletion of a shift

The following example shows how to stage the deletion of a **shift** in a **schedule** in draft mode.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
POST https://graph.microsoft.com/v1.0/teams/3d88b7a2-f988-4f4b-bb34-d66df66af126/schedule/shifts/SHFT_577b75d2-a927-48c0-a5d1-dc984894e7b8/stageForDeletion
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/teams/3d88b7a2-f988-4f4b-bb34-d66df66af126/schedule/shifts/SHFT_577b75d2-a927-48c0-a5d1-dc984894e7b8/stageForDeletion')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 3: Stage the deletion of a timeOff

The following example shows how to stage the deletion of a **timeOff** in a **schedule** in draft mode.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [JavaScript](#tabpanel_3_javascript)

```http
POST https://graph.microsoft.com/v1.0/teams/3d88b7a2-f988-4f4b-bb34-d66df66af126/schedule/timesOff/SHFT_577b75d2-a927-48c0-a5d1-dc984894e7b8/stageForDeletion
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/teams/3d88b7a2-f988-4f4b-bb34-d66df66af126/schedule/timesOff/SHFT_577b75d2-a927-48c0-a5d1-dc984894e7b8/stageForDeletion')
	.post();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
