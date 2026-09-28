<!-- Source: https://learn.microsoft.com/en-us/graph/api/schedulechangerequest-approveforuser?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-06-03 -->

# scheduleChangeRequest: approveForUser

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Approve a [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-beta) object for a user. This action only supports application permissions.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Permissions for [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-beta):

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

Permissions for [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-beta):

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

Permissions for [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-beta):

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

Permissions for [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-beta):

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Schedule.ReadWrite.All | Not available. |

## HTTP request

To approve an [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-beta) object for a user.

```http
POST /teams/{teamsId}/schedule/offerShiftRequests/{offerShiftRequestId}/approveForUser
```

To approve an [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-beta) object for a user.

```http
POST /teams/{teamsId}/schedule/openShiftChangeRequests/{openShiftChangeRequestId}/approveForUser
```

To approve a [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-beta) object for a user.

```http
POST /teams/{teamId}/schedule/swapShiftsChangeRequests/{swapShiftChangeRequestId}/approveForUser
```

To approve a [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-beta) object for a user.

```http
POST /teams/{teamsId}/schedule/timeOffRequests/{timeOffRequestId}/approveForUser
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| message | String | Custom message sent on approval. Optional. |
| userId | String | ID of the user who approved the request. Required. |

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Example 1: Approve an offer shift request for a user

The following example shows how to approve an [offerShiftRequest](https://learn.microsoft.com/en-us/graph/api/resources/offershiftrequest?view=graph-rest-beta) for a user. Only the assignee can approve the request. For details, see the **assignedTo** property in [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-beta).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/teams/8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/schedule/offerShiftRequests/SREQ_bb7af804-9ca1-48d7-9a0c-aa5a9f447d3c/approveForUser
Content-Type: application/json

{
  "message": "Approved!",
  "userId": "d2e7b5b2-0355-4c73-a543-08847b5b0884"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const approveForUser = {
  message: 'Approved!',
  userId: 'd2e7b5b2-0355-4c73-a543-08847b5b0884'
};

await client.api('/teams/8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/schedule/offerShiftRequests/SREQ_bb7af804-9ca1-48d7-9a0c-aa5a9f447d3c/approveForUser')
	.version('beta')
	.post(approveForUser);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 2: Approve an open shift change request for a user

The following example shows how to approve an [openShiftChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/openshiftchangerequest?view=graph-rest-beta) for a user. The **userId** must be a team owner.

#### Request

The following example shows a request.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
POST https://graph.microsoft.com/beta/teams/8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/schedule/openShiftChangeRequests/SREQ_8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/approveForUser
Content-Type: application/json

{
  "message": "Approved.",
  "userId": "d2e7b5b2-0355-4c73-a543-08847b5b0884"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const approveForUser = {
  message: 'Approved.',
  userId: 'd2e7b5b2-0355-4c73-a543-08847b5b0884'
};

await client.api('/teams/8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/schedule/openShiftChangeRequests/SREQ_8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/approveForUser')
	.version('beta')
	.post(approveForUser);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 3: Approve a swap shift change request for a user

The following example shows how to approve a [swapShiftsChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/swapshiftschangerequest?view=graph-rest-beta) for a user. Only the assignee can approve the request. For details, see the **assignedTo** property in [scheduleChangeRequest](https://learn.microsoft.com/en-us/graph/api/resources/schedulechangerequest?view=graph-rest-beta).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_3_http)
- [JavaScript](#tabpanel_3_javascript)

```http
POST /teams/8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/schedule/swapShiftsChangeRequests/SREQ_8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/approveForUser
Content-Type: application/json

{
  "message": "Approved.",
  "userId": "d2e7b5b2-0355-4c73-a543-08847b5b0884"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const approveForUser = {
  message: 'Approved.',
  userId: 'd2e7b5b2-0355-4c73-a543-08847b5b0884'
};

await client.api('/teams/8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/schedule/swapShiftsChangeRequests/SREQ_8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/approveForUser')
	.version('beta')
	.post(approveForUser);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

### Example 4: Approve a time off request for a user

The following example shows how to approve a [timeOffRequest](https://learn.microsoft.com/en-us/graph/api/resources/timeoffrequest?view=graph-rest-beta) for a user. The **userId** must be a team owner \(manager\).

#### Request

The following example shows a request.

- [HTTP](#tabpanel_4_http)
- [JavaScript](#tabpanel_4_javascript)

```http
POST https://graph.microsoft.com/beta/teams/8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/schedule/timeOffRequests/SREQ_bb7af804-9ca1-48d7-9a0c-aa5a9f447d3c/approveForUser
Content-Type: application/json

{
  "message": "Approved!",
  "userId": "d2e7b5b2-0355-4c73-a543-08847b5b0884"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const approveForUser = {
  message: 'Approved!',
  userId: 'd2e7b5b2-0355-4c73-a543-08847b5b0884'
};

await client.api('/teams/8f23a3b1-b87f-4a62-b38f-24a5fa83fa29/schedule/timeOffRequests/SREQ_bb7af804-9ca1-48d7-9a0c-aa5a9f447d3c/approveForUser')
	.version('beta')
	.post(approveForUser);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
