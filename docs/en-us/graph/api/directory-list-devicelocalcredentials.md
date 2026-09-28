<!-- Source: https://learn.microsoft.com/en-us/graph/api/directory-list-devicelocalcredentials?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-25 -->

# List deviceLocalCredentialInfo

Namespace: microsoft.graph

Get a list of the [deviceLocalCredentialInfo](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredentialinfo?view=graph-rest-1.0) objects and their properties, excluding the [credentials](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredential?view=graph-rest-1.0) property.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | DeviceLocalCredential.ReadBasic.All | DeviceLocalCredential.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | DeviceLocalCredential.ReadBasic.All | DeviceLocalCredential.Read.All |

Important

In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with a supported role permission. The following least privileged roles are supported for this operation.

- Cloud Device Administrator
- Helpdesk Administrator
- Intune Service Administrator
- Security Administrator
- Security Reader
- Global Reader

## HTTP request

To get a list of **deviceLocalCredentialInfo** objects within the tenant:

```http
GET /directory/deviceLocalCredentials
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$search`, `$orderby`, `$top`, `$count` and `$skiptoken` OData query parameter to help customize the response.

The response might also contain an `odata.nextLink`, which you can use to page through the result set. For details, see [Paging Microsoft Graph data](https://learn.microsoft.com/en-us/graph/paging).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| User-Agent | The identifier for the calling application. This value contains information about the operating system and the browser used. Required. |
| ocp-client-name | The name of the client application performing the API call. This header is used for debugging purposes. Optional. |
| ocp-client-version | The version of the client application performing the API call. This header is used for debugging purposes. Optional. |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [deviceLocalCredentialInfo](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredentialinfo?view=graph-rest-1.0) objects, excluding the [credentials](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredential?view=graph-rest-1.0) properties, in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/directory/deviceLocalCredentials
User-Agent: "Dsreg/10.0 (Windows 10.0.19043.1466)"
ocp-client-name: "My Friendly Client"
ocp-client-version: "1.2"
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "b465e4e8-e4e8-b465-e8e4-65b4e8e465b4",
      "deviceName": "LAPS_TEST",
      "lastBackupDateTime": "2023-04-21T13:45:30.0000000Z",
      "refreshDateTime": "2020-05-20T13:45:30.0000000Z"
    },
    {
      "id": "c9a5d9e6-d2bd-4ff6-8a47-38b98800600c",
      "deviceName": "LAPS_TEST2",
      "lastBackupDateTime": "2023-04-21T13:45:30.0000000Z",
      "refreshDateTime": "2020-05-20T13:45:30.0000000Z"
    }
  ]
}
```
