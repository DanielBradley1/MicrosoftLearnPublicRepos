<!-- Source: https://learn.microsoft.com/en-us/graph/api/devicelocalcredentialinfo-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-26 -->

# Get deviceLocalCredentialInfo

Namespace: microsoft.graph

Retrieve the properties of a [deviceLocalCredentialInfo](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredentialinfo?view=graph-rest-1.0) for a specified device object.

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

To access the actual passwords on the device, done by including `$select=credentials` as part of the query parameters, the app must be assigned the *DeviceLocalCredential.Read.All* permission and *DeviceLocalCredential.ReadBasic.All* is insufficient.

Important

In delegated scenarios with work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role with a supported role permission. The following least privileged roles are supported for this operation.

- Cloud Device Administrator
- Helpdesk Administrator
- Intune Service Administrator
- Security Administrator
- Security Reader
- Global Reader

To access the actual passwords on the device by using the `$select=credentials` query parameter, the following least privileged roles are supported:

- Cloud Device Administrator
- Intune Service Administrator

## HTTP request

To get the device local credential for a specific device object:

```http
GET /directory/deviceLocalCredentials/{deviceId}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| User-Agent | The identifier for the calling application. This value contains information about the operating system and the browser used. Required. |
| ocp-client-name | The name of the client application performing the API call. This header is used for debugging purposes. Optional. |
| ocp-client-version | The version of the client application performing the API call. This header is used for debugging purposes. Optional. |

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [deviceLocalCredential](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredential?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Get a device's local administrator account credential info

#### Request

The following example shows a request. This example doesn't return the **credentials** property.

```http
GET https://graph.microsoft.com/v1.0/directory/deviceLocalCredentials/b465e4e8-e4e8-b465-e8e4-65b4e8e465b4
User-Agent: "Dsreg/10.0 (Windows 10.0.19043.1466)"
ocp-client-name: "My Friendly Client"
ocp-client-version: "1.2"
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.deviceLocalCredentialInfo",
    "id": "b465e4e8-e4e8-b465-e8e4-65b4e8e465b4",
    "deviceName": "LAPS_TEST",
    "lastBackupDateTime": "2023-04-21T13:45:30.0000000Z",
    "refreshDateTime": "2020-05-20T13:45:30.0000000Z"
  }
}
```

### Example 2: Get the device local administrator account credential info with the **credentials** property

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/directory/deviceLocalCredentials/b465e4e8-e4e8-b465-e8e4-65b4e8e465b4?$select=credentials
User-Agent: "Dsreg/10.0 (Windows 10.0.19043.1466)"
ocp-client-name: "My Friendly Client"
ocp-client-version: "1.2"
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.deviceLocalCredentialInfo",
    "id": "b465e4e8-e4e8-b465-e8e4-65b4e8e465b4",
    "deviceName": "LAPS_TEST",
    "lastBackupDateTime": "2023-04-21T13:45:30.0000000Z",
    "refreshDateTime": "2020-05-20T13:45:30.0000000Z",
    "credentials": [
      {
        "accountName": "ContosoLocalAdminAccount",
        "accountSid": "S-1-5-21-2318549658-1590267884-3984890135-1965",
        "backupDateTime": "2023-04-21T13:45:30.0000000Z",
        "passwordBase64": "UQBRAEAAZAA4AGYAOABnAFkA"
      },
      {
        "accountName": "ContosoLocalAdminAccount",
        "accountSid": "S-1-5-21-2318549658-1590267884-3984890135-1965",
        "backupDateTime": "2023-03-22T13:45:30.0000000Z",
        "passwordBase64": "KgBEADkAawBsAGsAZgAjADQA"
      },
      {
        "accountName": "Administrator",
        "accountSid": "S-1-5-21-2318549658-1590267884-3984890135-500",
        "backupDateTime": "2023-02-23T13:45:30.0000000Z",
        "passwordBase64": "TABwAGQAOQAqACgAKQAzADQA"
      }
    ]
  }
}
```
