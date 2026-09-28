<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-deployments-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-04 -->

# List deployment logs

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve a list of logs that includes the status of [deployments](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deployment?view=graph-rest-beta) performed through the Global Secure Access services.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | NetworkAccess.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | NetworkAccess.Read.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Global Secure Access Log Reader
- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
GET /networkAccess/deployments
```

## Optional query parameters

This method supports the `$filter` and `$select` OData query parameters to help customize the response. For more information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [deployment](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-deployment?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/networkAccess/deployments
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/deployments",
    "value": [
        {
                "requestId": "61addd7c-33ca-4737-93cc-2a3adc933562",
                "lastModifiedDateTime": "2025-01-19T21:26:35.0829571Z",
                "initiatedBy": "GSA Service account",
                "deploymentEndDateTime": "2025-01-19T21:29:39Z",
                "status": {
                    "deploymentStage": "succeeded",
                    "message": null
                },
                "configuration": {
                    "@odata.type": "#microsoft.graph.networkaccess.deploymentConfiguration",
                    "operationName": "Redistribute Forwarding Profile",
                    "changeType": "forwardingProfile"
                }
        }
    ]
}
```
