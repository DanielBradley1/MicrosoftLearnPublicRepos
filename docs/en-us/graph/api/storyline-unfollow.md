<!-- Source: https://learn.microsoft.com/en-us/graph/api/storyline-unfollow?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# storyline: unfollow

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Stop following a user's [storyline](https://learn.microsoft.com/en-us/graph/api/resources/storyline?view=graph-rest-beta). Removes the specified user from the signed-in user's following list.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Storyline.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Storyline.ReadWrite.All | Not available. |

## HTTP request

```http
POST /users/{user-id}/employeeExperience/storyline/unfollow
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

For **delegated** permissions \(user context\), leave the request body empty:

```json
{}
```

For **application** permissions \(app-only context\), provide the following parameter:

| Parameter | Type | Description |
| :--- | :--- | :--- |
| unfollowBy | [engagementIdentitySet](https://learn.microsoft.com/en-us/graph/api/resources/engagementidentityset?view=graph-rest-beta) | The identity information of the user who is unfollowing. Required for application permissions. |

## Response

If successful, this action returns a `204 No Content` response code.

## Examples

### Example 1: Unfollow a user with delegated permissions

The following example shows how to unfollow a user using delegated permissions.

#### Request

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/users/f2a84916-d735-41d9-a04a-4ecf6266ae71/employeeExperience/storyline/unfollow
Content-Type: application/json

{}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unfollow = {};

await client.api('/users/f2a84916-d735-41d9-a04a-4ecf6266ae71/employeeExperience/storyline/unfollow')
	.version('beta')
	.post(unfollow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```

### Example 2: Unfollow a user with application permissions

The following example shows how to unfollow a user using application permissions.

#### Request

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)

```http
POST https://graph.microsoft.com/beta/users/b3c29da7-ff83-4a92-b14e-7c91fe830b96/employeeExperience/storyline/unfollow
Content-Type: application/json

{
  "unfollowBy": {
    "user": {
      "id": "e7f439cd-2e84-4b15-a903-f6d82a7b9c21"
    }
  }
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const unfollow = {
  unfollowBy: {
    user: {
      id: 'e7f439cd-2e84-4b15-a903-f6d82a7b9c21'
    }
  }
};

await client.api('/users/b3c29da7-ff83-4a92-b14e-7c91fe830b96/employeeExperience/storyline/unfollow')
	.version('beta')
	.post(unfollow);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

```http
HTTP/1.1 204 No Content
```
