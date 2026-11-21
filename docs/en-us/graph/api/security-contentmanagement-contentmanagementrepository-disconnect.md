<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-disconnect?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# contentManagementRepository: disconnect

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Disconnect a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta). The provider **accessCredential** is optional: without it, the connection is still removed but repository-side artifacts may remain and are reported in **warning**. Remove the deployment identity to stop further pushes.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Repository.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Repository.ReadWrite.All | Not available. |

## HTTP request

```http
POST /security/contentManagement/repositories/{contentManagementRepositoryId}/microsoft.graph.security.contentManagement.disconnect
```

## Path parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| contentManagementRepositoryId | String | The service-generated identifier of the [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta). |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer token. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required when a JSON body is supplied. |

## Request body

The **accessCredential** parameter is optional. When supplied, it authorizes best-effort cleanup of repository-side artifacts; it isn't persisted or returned. Omit the request body to remove the connection without provider cleanup.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| accessCredential | [microsoft.graph.security.contentManagement.repositoryAccessCredential](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositoryaccesscredential?view=graph-rest-beta) | Optional. Provider credential for best-effort cleanup. |

## Response

If successful, this action returns a `200 OK` response code and a [microsoft.graph.security.contentManagement.repositoryDisconnectResult](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorydisconnectresult?view=graph-rest-beta) in the response body.

## Examples

### Request

```http
POST https://graph.microsoft.com/beta/security/contentManagement/repositories/5f8d1c2e-3b4a-4c9d-9e10-2a3b4c5d6e7f/microsoft.graph.security.contentManagement.disconnect
Content-Type: application/json

{
  "accessCredential": {
    "@odata.type": "#microsoft.graph.security.contentManagement.repositoryPatCredential",
    "token": "ghp_example_token"
  }
}
```

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.contentManagement.repositoryDisconnectResult",
  "warning": null
}
```
