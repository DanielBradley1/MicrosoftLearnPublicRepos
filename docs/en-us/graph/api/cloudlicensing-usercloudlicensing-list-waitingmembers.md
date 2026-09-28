<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudlicensing-usercloudlicensing-list-waitingmembers?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List waitingMembers for user

Namespace: microsoft.graph.cloudLicensing

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) objects granted to a user. This API returns details about licenses that are directly assigned to a user and those licenses transitively assigned through membership in licensed groups.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | User-UsageRight.Read | User.Read, User.Read.All, User.ReadWrite, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All, User-CloudLicensing.Read.All, User-CloudLicensing.Read, User-UsageRight.Read.All, User-UsageRight.Read |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | User-UsageRight.Read.All | User.Read.All, User.ReadWrite.All, Directory.Read.All, Directory.ReadWrite.All, User-CloudLicensing.Read.All, User-UsageRight.Read.All |

## HTTP request

To get all waiting members for the signed-in user using delegated \(`/me`\) permissions:

```http
GET /me/cloudLicensing/waitingMembers
```

To get all waiting members for a specific user using either delegated or application permissions:

```http
GET /users/{userId}/cloudLicensing/waitingMembers
```

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.cloudLicensing.waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) objects in the response body.

## Examples

The following example shows how to get all waiting members granted to a user.

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/beta/users/48fbdf70-9e09-40df-9dbe-17af483ab113/cloudLicensing/waitingMembers?$expand=allotment($select=id,skuId,skuPartNumber)
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let waitingMembers = await client.api('/users/48fbdf70-9e09-40df-9dbe-17af483ab113/cloudLicensing/waitingMembers')
	.version('beta')
	.expand('allotment($select=id,skuId,skuPartNumber)')
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
      "@odata.type": "#microsoft.graph.cloudLicensing.waitingMember",
      "id": "49caea1b-ad15-64f1-70c5-5c5e3563d19c",
      "waitingSinceDateTime": "2024-11-22T17:11:10.6635939+00:00",
      "allotment":
        {
          "@odata.type": "#microsoft.graph.cloudLicensing.allotment",
          "id": "551f1755-0184-9e51-0bc7-f32bae5a1afb",
          "skuId": "4b9405b0-7788-4568-add1-99614e613b69",
          "skuPartNumber": "EXCHANGESTANDARD"
        }  
    }
  ]
}
```
