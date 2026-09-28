<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-usageright-list-assignments?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List assignments for usageRight

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) objects which combine to form this [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta), including both direct assignments and assignments inherited through group membership.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

Permissions to list **usageRight** assignments for a user:

```http
GET /me/cloudLicensing/usageRights/{usageRightId}/assignments
GET /users/{userId}/cloudLicensing/usageRights/{usageRightId}/assignments
```

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User-CloudLicensing.Read | User-CloudLicensing.Read.All, Group-CloudLicensing.Read, Group-CloudLicensing.Read.All, User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | User-CloudLicensing.Read.All | Group-CloudLicensing.Read.All, User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |

Permissions to list **usageRight** assignments for a group:

```http
GET /groups/{groupId}/cloudLicensing/usageRights/{usageRightId}/assignments
```

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Group-UsageRight.Read.All | Directory.Read.All, Directory.ReadWrite.All, Group-CloudLicensing.Read, Group-CloudLicensing.Read.All, Group.Read.All, Group.ReadWrite.All, User.Read.All, User.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Group-UsageRight.Read.All | Directory.Read.All, Directory.ReadWrite.All, Group-CloudLicensing.Read.All, Group.Read.All, Group.ReadWrite.All, User.Read.All, User.ReadWrite.All |

## HTTP request

To list assignments for the signed-in user using delegated \(`/me`\) permissions:

```http
GET /me/cloudLicensing/usageRights/{usageRightId}/assignments
```

To list assignments using either delegated or application permissions:

```http
GET /groups/{groupId}/cloudLicensing/usageRights/{usageRightId}/assignments
GET /users/{userId}/cloudLicensing/usageRights/{usageRightId}/assignments
```

## Optional query parameters

This method supports the `$select`, `$top`, and `$expand` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.cloudLicensing.assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/beta/me/cloudLicensing/usageRights/7e452304-0a58-40d6-8fd2-2afe92d26a3a/assignments
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let assignments = await client.api('/me/cloudLicensing/usageRights/7e452304-0a58-40d6-8fd2-2afe92d26a3a/assignments')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.cloudLicensing.assignment",
      "id": "405ee855-dd74-f695-8d7e-be35a6788fe8",
      "disabledServicePlanIds": [
        "5e62787c-c316-451f-b873-1d05acd4d12c"
      ]
    }
  ]
}
```
