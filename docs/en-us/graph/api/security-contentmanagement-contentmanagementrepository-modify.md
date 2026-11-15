<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-modify?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# contentManagementRepository: modify

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Modify a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta). Changing **contentTypes** requires **accessCredential** to revalidate provider access; display-name and description changes don't.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Repository.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /security/contentManagement/repositories/{contentManagementRepositoryId}/microsoft.graph.security.contentManagement.modify
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

In the request body, supply a JSON representation of the parameters. Only **displayName**, **description**, **contentTypes**, and **accessCredential** can be changed. **repoType**, **sourceLocation**, **deploymentScope**, and **deploymentIdentity** are immutable and rejected when supplied.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Optional. Human-readable name of the connection. |
| description | String | Optional. Description of the connection. |
| contentTypes | [microsoft.graph.security.contentManagement.repositoryContentType](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-contentmanagement?view=graph-rest-beta#repositorycontenttype-values) collection | Optional. Content kinds this repository is configured to deploy. Requires **accessCredential** to revalidate provider access. |
| accessCredential | [microsoft.graph.security.contentManagement.repositoryAccessCredential](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositoryaccesscredential?view=graph-rest-beta) | Optional. Provider credential requests republishing; metadata-only changes do not require it. Write-only; never returned. |

## Response

If successful, this action returns a `200 OK` response code and a [microsoft.graph.security.contentManagement.contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) in the response body.

## Examples

### Request

```http
POST https://graph.microsoft.com/beta/security/contentManagement/repositories/5f8d1c2e-3b4a-4c9d-9e10-2a3b4c5d6e7f/microsoft.graph.security.contentManagement.modify
Content-Type: application/json

{
  "displayName": "Contoso detections and hunting",
  "contentTypes": [
    "customDetection"
  ],
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
  "@odata.type": "#microsoft.graph.security.contentManagement.contentManagementRepository",
  "id": "5f8d1c2e-3b4a-4c9d-9e10-2a3b4c5d6e7f",
  "displayName": "Contoso detections and hunting",
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
