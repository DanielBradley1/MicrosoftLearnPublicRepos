<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-waitingmember-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# Get waitingMember

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Read the properties and relationships of [waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudLicensing.Read | CloudLicensing.Read.All, User-CloudLicensing.Read, User-CloudLicensing.Read.All, User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudLicensing.Read.All | User-CloudLicensing.Read.All, User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All |

## HTTP request

To get a waiting member for the signed-in user using delegated \(`/me`\) permissions:

```http
GET /me/cloudLicensing/waitingMembers/{waitingMemberId}
```

To get a waiting member using either delegated or application permissions:

```http
GET /admin/cloudLicensing/allotments/{allotmentId}/waitingMembers/{waitingMemberId}
GET /users/{userId}/cloudLicensing/waitingMembers/{waitingMemberId}
```

## Optional query parameters

This method supports the `$select` and `$expand` OData query parameters to customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.cloudLicensing.waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/beta/users/48fbdf70-9e09-40df-9dbe-17af483ab113/cloudLicensing/waitingMembers/f2c588fc-0a33-4f95-806b-58678112b1a9?$expand=assignedTo
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let waitingMember = await client.api('/users/48fbdf70-9e09-40df-9dbe-17af483ab113/cloudLicensing/waitingMembers/f2c588fc-0a33-4f95-806b-58678112b1a9')
	.version('beta')
	.expand('assignedTo')
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
  "value": {
    "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
    "id": "49caea1b-ad15-64f1-70c5-5c5e3563d19c",
    "waitingSinceDateTime": "2024-11-22T17:11:10.6635939+00:00",
    "assignedTo": {
      "@odata.type": "#microsoft.graph.user",
      "id": "a6c034b8-621b-dee3-6abb-52cbce801fe9",
      "displayName": "Steve Fred",
      "userPrincipalName": "stevefred@contoso.com"
    }
  }
}
```
