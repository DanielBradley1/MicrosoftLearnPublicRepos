<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcmanagedlicense-retrievemanagedlicenseoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# cloudPcManagedLicense: retrieveManagedLicenseOperation

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Retrieve the status and per-user results of a previously submitted operation on the [cloudPcManagedLicense](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicense?view=graph-rest-beta) collection. Use the service-generated **operationRequestId** returned by the [submitManagedLicenseOperation](https://learn.microsoft.com/en-us/graph/api/cloudpcmanagedlicense-submitmanagedlicenseoperation?view=graph-rest-beta) request.

This function is bound to the managed-license collection and doesn't require an individual managed-license ID. It has no side effects. Submitted operations don't currently expire and aren't scheduled for deletion.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.Read.All | CloudPC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.Read.All | CloudPC.ReadWrite.All |

> **Note:** For delegated access, the signed-in user must also have the Cloud PC RBAC permission `Microsoft.CloudPC/ManagedLicenseOperations/Read`.

## HTTP request

```http
GET /deviceManagement/virtualEndpoint/managedLicenses/retrieveManagedLicenseOperation(operationRequestId='{operationRequestId}')
```

## Function parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| operationRequestId | String | Required. The service-generated operation request ID returned by the [submitManagedLicenseOperation](https://learn.microsoft.com/en-us/graph/api/cloudpcmanagedlicense-submitmanagedlicenseoperation?view=graph-rest-beta) request. |

## Optional query parameters

This method doesn't support the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [cloudPcManagedLicenseOperation](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseoperation?view=graph-rest-beta) object in the response body. Currently, the result is a [cloudPcManagedLicenseExtendAccess](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseextendaccess?view=graph-rest-beta) object.

If **operationStatus** is `inProgress`, the **results** collection is empty. When the operation reaches a terminal status, the collection contains one result for each user identifier supplied in **entraUserIds**. Each result indicates whether the user's operation succeeded or failed; a failed result also includes **failureCode**.

This function can also return the following response codes.

| HTTP status code | Description |
| :--- | :--- |
| 403 Forbidden | The tenant isn't licensed, or the information for the tenant wasn't synchronized. |
| 404 Not Found | The operation request ID doesn't identify an existing operation. |
| 429 Too Many Requests | The request is throttled. |

For per-user failures in a completed operation, inspect the **failureCode** property of each [cloudPcManagedLicenseOperationResult](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseoperationresult?view=graph-rest-beta) object.

## Examples

### Request

The following example retrieves a previously submitted operation by its operation request ID.

```http
GET https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/managedLicenses/retrieveManagedLicenseOperation(operationRequestId='6e2f7a9c-1d3b-4e5f-8a6b-2c4d6e8f0a1b')
```

### Response

The following example shows a completed operation with one succeeded result and one failed result.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.cloudPcManagedLicenseOperation",
  "@odata.type": "#microsoft.graph.cloudPcManagedLicenseExtendAccess",
  "operationRequestId": "6e2f7a9c-1d3b-4e5f-8a6b-2c4d6e8f0a1b",
  "entraUserIds": [
    "1a13832e-cd79-497d-be76-24186f55c8b0",
    "2b24943f-de8a-508e-cf87-35297f66d9c1"
  ],
  "servicePlanId": "3a94476b-504b-41a4-9f6a-18c5199a55e9",
  "createdDateTime": "2026-10-09T09:00:00Z",
  "operationStatus": "partiallySucceeded",
  "results": [
    {
      "entraUserId": "1a13832e-cd79-497d-be76-24186f55c8b0",
      "operationResultStatus": "succeeded"
    },
    {
      "entraUserId": "2b24943f-de8a-508e-cf87-35297f66d9c1",
      "operationResultStatus": "failed",
      "failureCode": "noEligibleLicenseAvailable"
    }
  ]
}
```
