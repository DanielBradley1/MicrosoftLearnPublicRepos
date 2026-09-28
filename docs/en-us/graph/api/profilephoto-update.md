<!-- Source: https://learn.microsoft.com/en-us/graph/api/profilephoto-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Update profilePhoto

Namespace: microsoft.graph

Update the photo for the specified contact, group, team, or user in a tenant. The size of the photo you can update to is limited to 4 MB.

You can use either PATCH or PUT for this operation.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

The following tables show the least privileged permission or permissions required to call this API on each supported resource type. Follow [best practices](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions) to request least privileged permissions. For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

### To update the profile photo of a contact

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Contacts.ReadWrite | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Contacts.ReadWrite | Not supported. |

### To update the profile photo of a group

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ProfilePhoto.ReadWrite.All | Group.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | ProfilePhoto.ReadWrite.All | Group.ReadWrite.All |

### To update the profile photo of a team

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamSettings.ReadWrite.All | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamSettings.ReadWrite.All | Not supported. |

### To update the profile photo of a user

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | ProfilePhoto.ReadWrite.All | User.ReadWrite, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | User.ReadWrite | Not supported. |
| Application | ProfilePhoto.ReadWrite.All | User.ReadWrite.All |

Note

- Users with admin roles such as User admins, Global admins, or People admins can update the photo of any user in the organization by using delegated permissions. This operation is also supported with application permissions. Updating the photo of any user in the organization requires *ProfilePhoto.ReadWrite.All* or *User.ReadWrite.All* permission. Updating the photo of the signed-in user only requires *User.ReadWrite* permission.
- Updating a user's photo using the Microsoft Graph API is currently not supported in Azure AD B2C tenants.

## HTTP request

To update a contact's profile photo:

```http
PATCH /me/contacts/{id}/photo/$value
PATCH /users/{id | userPrincipalName}/contacts/{id}/photo/$value
PATCH /me/contactfolders/{contactFolderId}/contacts/{id}/photo/$value
PATCH /users/{id | userPrincipalName}/contactfolders/{contactFolderId}/contacts/{id}/photo/$value

PUT /me/contacts/{id}/photo/$value
PUT /users/{id | userPrincipalName}/contacts/{id}/photo/$value
PUT /me/contactfolders/{contactFolderId}/contacts/{id}/photo/$value
PUT /users/{id | userPrincipalName}/contactfolders/{contactFolderId}/contacts/{id}/photo/$value
```

To update a group photo:

```http
PATCH /groups/{id}/photo/$value

PUT /groups/{id}/photo/$value
```

To update a team photo:

```http
PUT /teams/{id}/photo/$value
```

To update a user's profile photo:

```http
PATCH /me/photo/$value
PATCH /users/{id | userPrincipalName}/photo/$value

PUT /me/photo/$value
PUT /users/{id | userPrincipalName}/photo/$value
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | image/jpeg. Required. |

## Request body

In the request body, include the binary data of the photo.

## Response

If successful, this method returns a `200 OK` response code or a `204 No Content` response code for updating the photo of a **team**.

## Examples

### Example 1: Update the photo of a user

#### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)
- [PowerShell](#tabpanel_1_powershell)

```http
PUT https://graph.microsoft.com/v1.0/me/photo/$value
Content-type: image/jpeg

Binary data for the image
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stream = Binary data for the image;

await client.api('/me/photo/$value')
	.put(stream);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Users

$params = Binary data for the image

# A UPN can also be used as -UserId.
Set-MgUserPhotoContent -UserId $userId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```

### Example 2: Update the photo of a team

#### Request

The following example shows a request to update a team photo.

- [HTTP](#tabpanel_2_http)
- [JavaScript](#tabpanel_2_javascript)
- [PowerShell](#tabpanel_2_powershell)

```http
PUT https://graph.microsoft.com/v1.0/teams/172b0cce-e65d-44ce-9a49-91d9f2e8491e/photo/$value
Content-type: image/jpeg

Binary data for the image
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const stream = Binary data for the image;

await client.api('/teams/172b0cce-e65d-44ce-9a49-91d9f2e8491e/photo/$value')
	.put(stream);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Teams

$params = Binary data for the image

Set-MgTeamPhotoContent -TeamId $teamId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
