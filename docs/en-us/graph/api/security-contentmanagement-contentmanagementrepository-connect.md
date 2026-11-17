<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-connect?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# contentManagementRepository: connect

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Connect a source-control repository to deliver security content as code. The provider **accessCredential** is write-only and isn't returned.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Repository.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Repository.ReadWrite.All | Not available. |

Note

When connecting with a personal access token, installing the GitHub App is optional. Install the [Azure-Sentinel GitHub App](https://github.com/apps/azure-sentinel) to view deployment status in Microsoft Defender. Grant it access to the connected repository.

Without a verified installation, deployments can run, but their status is unavailable.

If you install the App after connecting, call [modify](https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-modify?view=graph-rest-beta) with a valid **accessCredential**. This refreshes the connection's GitHub App binding.

## HTTP request

```http
POST /security/contentManagement/repositories/microsoft.graph.security.contentManagement.connect
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
| displayName | String | Required. Human-readable name of the connection. |
| repoType | [microsoft.graph.security.contentManagement.repositoryType](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-contentmanagement?view=graph-rest-beta#repositorytype-values) | Required. Source-control provider for this repository. |
| contentTypes | [microsoft.graph.security.contentManagement.repositoryContentType](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-contentmanagement?view=graph-rest-beta#repositorycontenttype-values) collection | Required. Content kinds this repository is configured to deploy. |
| sourceLocation | [microsoft.graph.security.contentManagement.repositorySettings](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorysettings?view=graph-rest-beta) | Required. Location of the source repository \(URL and branch\). |
| accessCredential | [microsoft.graph.security.contentManagement.repositoryAccessCredential](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositoryaccesscredential?view=graph-rest-beta) | Required. Provider credential supplied when connecting the repository. Write-only; never returned. |
| deploymentScope | [microsoft.graph.security.contentManagement.deploymentScope](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-deploymentscope?view=graph-rest-beta) | Optional. Azure deployment scope; its **id** is an ARM resource identifier. |
| description | String | Optional. Description of the connection. |
| deploymentIdentity | [microsoft.graph.security.contentManagement.deploymentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-deploymentidentity?view=graph-rest-beta) | Optional. Bring-your-own service principal or managed identity; when omitted, the platform-managed identity path is used. |

## Response

If successful, this action returns a `200 OK` response code and a [microsoft.graph.security.contentManagement.contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) in the response body.

## Examples

### Request

```http
POST https://graph.microsoft.com/beta/security/contentManagement/repositories/microsoft.graph.security.contentManagement.connect
Content-Type: application/json

{
  "displayName": "Contoso detections",
  "description": "Detection-as-code content for Contoso",
  "repoType": "gitHub",
  "contentTypes": [
    "customDetection"
  ],
  "sourceLocation": {
    "url": "https://github.com/contoso/detections",
    "branch": "main"
  },
  "deploymentIdentity": {
    "@odata.type": "#microsoft.graph.security.contentManagement.servicePrincipalDeploymentIdentity",
    "applicationId": "00000000-1111-2222-3333-444444444444"
  },
  "deploymentScope": {
    "scopeType": "managementGroup",
    "id": "/providers/Microsoft.Management/managementGroups/contoso-secops"
  },
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
