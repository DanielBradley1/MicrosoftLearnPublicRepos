<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamsadministration-telephonenumberlongrunningoperation-get?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-27 -->

# Get telephoneNumberLongRunningOperation

Namespace: microsoft.graph.teamsAdministration

Read the properties and relationships of [microsoft.graph.teamsAdministration.telephoneNumberLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-telephonenumberlongrunningoperation?view=graph-rest-1.0) object. This method is used to query the status of an assign or unassign number action using Graph API. This link is returned in the Location response header found in assign or unassign operation result.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsTelephoneNumber.Read.All | TeamsTelephoneNumber.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsTelephoneNumber.Read.All | TeamsTelephoneNumber.ReadWrite.All |

## HTTP request

```http
GET /admin/teams/telephoneNumberManagement/operations/{telephoneNumberLongRunningOperationId}
```

## Optional query parameters

None.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.teamsAdministration.telephoneNumberLongRunningOperation](https://learn.microsoft.com/en-us/graph/api/resources/teamsadministration-telephonenumberlongrunningoperation?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/operations{'QXNzaWdubWVudHw2Y2E4Yjc0Ni00YzgxLTRhY2EtOTUyNi1jZmNjNGRiYWYyMmI'}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": {
    "@odata.type": "#microsoft.graph.teamsAdministration.telephoneNumberLongRunningOperation",
    "id": "QXNzaWdubWVudHw2Y2E4Yjc0Ni00YzgxLTRhY2EtOTUyNi1jZmNjNGRiYWYyMmI",
    "createdDateTime": "2025-02-03T22:03:26Z",
    "status": "succeeded",
    "numbers": [
      {
        "resourceLocation": "https://graph.microsoft.com/v1.0/admin/teams/telephoneNumberManagement/numberAssignments/N2EyMDUxOTctOGU1OS00ODdkLWI5ZmEtM2ZjMWIxMDhmMWU1fCsxMjA2MTIzNDU2Nw",
        "status": "succeeded"
      }
    ]
  }
}
```
