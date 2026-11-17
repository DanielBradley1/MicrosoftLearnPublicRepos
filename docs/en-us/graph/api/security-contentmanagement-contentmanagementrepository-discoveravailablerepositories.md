<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-discoveravailablerepositories?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# contentManagementRepository: discoverAvailableRepositories

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Discover source-control repositories accessible through a supplied write-only **accessCredential**. The result contains up to 200 transient candidates and isn't paged.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Repository.Read.All | Repository.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Repository.Read.All | Repository.ReadWrite.All |

## HTTP request

```http
POST /security/contentManagement/repositories/microsoft.graph.security.contentManagement.discoverAvailableRepositories
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer token. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required when a JSON body is supplied. |

## Request body

In the request body, supply a JSON representation of the parameters. The following table describes the supported parameters.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| accessCredential | [microsoft.graph.security.contentManagement.repositoryAccessCredential](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositoryaccesscredential?view=graph-rest-beta) | Required. Provider credential authorizing repository discovery. Not persisted; used only for this call. Write-only; never returned. |

## Response

If successful, this action returns a `200 OK` response code and a collection of [microsoft.graph.security.contentManagement.discoveredRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-discoveredrepository?view=graph-rest-beta) objects in the response body.

## Examples

### Request

```http
POST https://graph.microsoft.com/beta/security/contentManagement/repositories/microsoft.graph.security.contentManagement.discoverAvailableRepositories
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
  "value": [
    {
      "@odata.type": "#microsoft.graph.security.contentManagement.discoveredRepository",
      "url": "https://github.com/contoso/detections",
      "fullName": "contoso/detections",
      "branches": [
        "main",
        "dev"
      ]
    }
  ]
}
```
