<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpc-retrieveflexcloudpcconfigurationdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# cloudPC: retrieveFlexCloudPcConfigurationDetail

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get Windows 365 Flex \(formerly Windows 365 Frontline\) configuration details for a [Cloud PC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta), including license availability. The [cloudPcFlexConfigurationDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcflexconfigurationdetail?view=graph-rest-beta) response indicates whether a Flex license is available, based on the service plan and concurrent-access group for the Cloud PC.

This function retrieves license availability, not the power state of the Cloud PC. To retrieve its live access state, use [retrieveFlexCloudPcAccessConfiguration](https://learn.microsoft.com/en-us/graph/api/cloudpc-retrieveflexcloudpcaccessconfiguration?view=graph-rest-beta).

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.Read.All | CloudPC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.Read.All | CloudPC.ReadWrite.All |

Note

For delegated access, the signed-in user must also have the `Microsoft.CloudPC/CloudPCs/Read` permission through Windows 365 role-based access control \(RBAC\). For application access, the application must be authorized for the Cloud PC tenant.

## HTTP request

```http
GET /deviceManagement/virtualEndpoint/cloudPCs/{cloudPCId}/retrieveFlexCloudPcConfigurationDetail
```

## Optional query parameters

This method doesn't support the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [cloudPcFlexConfigurationDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcflexconfigurationdetail?view=graph-rest-beta) in the response body.

This function can also return the following errors.

| Status code | Condition |
| :--- | :--- |
| `400 Bad Request` | The Cloud PC identifier is malformed or the Cloud PC isn't supported by the Flex configuration-detail flow, including non-Flex Cloud PCs. |
| `500 Internal Server Error` | The service can't resolve the Cloud PC or retrieve its Flex license availability from a downstream service. |

For information about other errors, see [Microsoft Graph error responses](https://learn.microsoft.com/en-us/graph/errors).

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/cloudPCs/8c8a1f00-9a46-4f68-a8be-8713985c4576/retrieveFlexCloudPcConfigurationDetail
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.cloudPcFlexConfigurationDetail",
  "flexCloudPcAvailability": "available"
}
```
