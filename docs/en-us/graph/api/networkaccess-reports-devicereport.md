<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-reports-devicereport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# reports: deviceReport

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provide a report of all devices with network traffic that the [Global Secure Access services](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-global-secure-access-api-overview?view=graph-rest-beta) captured.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccessPolicy.Read.All | NetworkAccessPolicy.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Global Secure Access Log Reader
- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
GET /networkAccessRoot/reports/deviceReport(startDateTime={startDateTime}, endDateTime={endDateTime})
```

## Function parameters

In the request URL, provide the following query parameters with values. The following table shows the parameters that can be used with this function.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| startDateTime | DateTimeOffset | The time and date of the beginning of the report period. |
| endDateTime | DateTimeOffset | The time and date of the end of the report period. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [microsoft.graph.networkaccess.device](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-device?view=graph-rest-beta) collection in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/networkaccess/reports/deviceReport(startDateTime=2023-08-20T12:12:59.076Z, endDateTime=2023-08-21T12:12:59.076Z) 
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let deviceReport = await client.api('/networkaccess/reports/deviceReport(startDateTime=2023-08-20T12:12:59.076Z, endDateTime=2023-08-21T12:12:59.076Z)')
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
  "@odata.context":"https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.networkaccess.device)",
  "value":[
     {
        "displayName":"john's device",
        "deviceId":"253ba0d4-b3b0-4825-8cd8-0f5338fade6a",
        "operatingSystem":"Windows 11 Pro",
        "isCompliant":true,
        "trafficType":"microsoft365",
        "lastAccessDateTime":"2023-08-09T13:20:04Z"
     },
     {
        "displayName":"john's device",
        "deviceId":"253ba0d4-b3b0-4825-8cd8-0f5338fade6a",
        "operatingSystem":"Windows 11 Pro",
        "isCompliant":true,
        "trafficType":"private",
        "lastAccessDateTime":"2023-08-09T13:20:04Z"
     }
  ]
}
```
