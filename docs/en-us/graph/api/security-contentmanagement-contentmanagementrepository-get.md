<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Get contentManagementRepository

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) by its service-generated identifier.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Repository.Read.All | Repository.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Repository.Read.All | Repository.ReadWrite.All |

## HTTP request

```http
GET /security/contentManagement/repositories/{contentManagementRepositoryId}
```

## Optional query parameters

This method supports `$select`. It doesn't support `$search`, `$expand`, or delta queries.

## Path parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| contentManagementRepositoryId | String | The service-generated identifier of the [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta). |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer token. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.security.contentManagement.contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) in the response body.

## Examples

### Request

```http
GET https://graph.microsoft.com/beta/security/contentManagement/repositories/5f8d1c2e-3b4a-4c9d-9e10-2a3b4c5d6e7f
```

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.security.contentManagement.contentManagementRepository",
  "id": "5f8d1c2e-3b4a-4c9d-9e10-2a3b4c5d6e7f",
  "displayName": "Contoso detections",
  "description": "Detection-as-code content for Contoso",
  "repoType": "gitHub",
  "contentTypes": [
    "customDetection"
  ],
  "sourceLocation": {
    "url": "https://github.com/contoso/detections",
    "branch": "main",
    "deploymentLogsUrl": null
  },
  "deploymentIdentity": {
    "@odata.type": "#microsoft.graph.security.contentManagement.servicePrincipalDeploymentIdentity",
    "applicationId": "00000000-1111-2222-3333-444444444444"
  },
  "deploymentScope": {
    "scopeType": "managementGroup",
    "id": "/providers/Microsoft.Management/managementGroups/contoso-secops"
  },
  "servicePrincipal": null,
  "workloadIdentityFederation": null,
  "lastDeploymentInfo": null,
  "pullRequest": null,
  "systemData": null
}
```
