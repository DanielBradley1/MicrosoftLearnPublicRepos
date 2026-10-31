<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcmanagedlicense-submitmanagedlicenseoperation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# cloudPcManagedLicense: submitManagedLicenseOperation

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Submit an asynchronous operation on the [cloudPcManagedLicense](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicense?view=graph-rest-beta) collection to extend Windows 365 Reserve access for specified users. Currently, this action supports only the [cloudPcManagedLicenseExtendAccess](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseextendaccess?view=graph-rest-beta) derived type that extends Windows 365 Reserve access for specified users.

This action is bound to the managed-license collection and doesn't require an individual managed-license ID. The **servicePlanId** in the operation payload selects the target license SKU.

The action isn't idempotent. Each accepted request starts a separate operation with a service-generated **operationRequestId**. Resubmitting the same payload starts another operation and, for each user whose operation succeeds, adds another 10 days of access.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.ReadWrite.All | Not available. |

> **Note:** For delegated access, the signed-in user must also have the Cloud PC RBAC permission `Microsoft.CloudPC/ManagedLicenseOperations/Create`.

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/managedLicenses/submitManagedLicenseOperation
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| operation | [cloudPcManagedLicenseOperation](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseoperation?view=graph-rest-beta) | Required. The operation to submit. Currently, only the [cloudPcManagedLicenseExtendAccess](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseextendaccess?view=graph-rest-beta) derived type is supported. |

For an extend-access operation, set the **@odata.type** property to `#microsoft.graph.cloudPcManagedLicenseExtendAccess` and supply the required **servicePlanId** and **entraUserIds** properties. The **entraUserIds** collection accepts a maximum of 1,000 Microsoft Entra user object identifiers. Duplicate values aren't allowed. Don't supply the service-computed **operationRequestId**, **createdDateTime**, **operationStatus**, or **results** properties.

## Response

If successful, this action returns a `202 Accepted` response code and a [cloudPcManagedLicenseOperation](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseoperation?view=graph-rest-beta) object in the response body. The result is a [cloudPcManagedLicenseExtendAccess](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmanagedlicenseextendaccess?view=graph-rest-beta) object with **operationStatus** set to `inProgress` and an empty **results** collection.

The `Location` response header contains the URL for [retrieveManagedLicenseOperation](https://learn.microsoft.com/en-us/graph/api/cloudpcmanagedlicense-retrievemanagedlicenseoperation?view=graph-rest-beta), including the service-generated **operationRequestId**. Save the operation request ID and use that function to poll for the status and per-user results.

If the calling application loses the `202 Accepted` response, this API can't recover the original operation request ID or retrieve the detailed results of the operation without it. Before resubmitting, an administrator can check the **Days left** value for the affected users' Reserve Cloud PCs in the Microsoft Intune admin center to see whether their available access time increased.

This action can also return the following response codes.

| HTTP status code | Description |
| :--- | :--- |
| 400 Bad Request | The operation payload is invalid or unsupported, or more than 1,000 user identifiers are submitted. |
| 403 Forbidden | The tenant isn't licensed, or the information for the tenant wasn't synchronized. |
| 429 Too Many Requests | The request is throttled. |

An invalid user identifier or an identifier for a user outside the tenant associated with the calling application doesn't fail the entire accepted operation; instead, the operation returns a failed per-user result for that identifier.

For an accepted operation, inspect the **results** collection after processing completes to identify any per-user failures and their **failureCode** values. For example, extending access beyond a total of 30 days returns `maximumAccessDurationExceeded` for the affected user.

## Examples

### Request

The following example submits an operation to extend access for two users.

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/managedLicenses/submitManagedLicenseOperation
Content-Type: application/json

{
  "operation": {
    "@odata.type": "#microsoft.graph.cloudPcManagedLicenseExtendAccess",
    "entraUserIds": [
      "1a13832e-cd79-497d-be76-24186f55c8b0",
      "2b24943f-de8a-508e-cf87-35297f66d9c1"
    ],
    "servicePlanId": "3a94476b-504b-41a4-9f6a-18c5199a55e9"
  }
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json
Location: https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/managedLicenses/retrieveManagedLicenseOperation(operationRequestId='6e2f7a9c-1d3b-4e5f-8a6b-2c4d6e8f0a1b')

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
  "operationStatus": "inProgress",
  "results": []
}
```
