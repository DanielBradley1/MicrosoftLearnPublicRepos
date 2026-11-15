<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# contentManagementRepository resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a connected source-control repository that delivers security content as code in the caller's tenant.

Inherits from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List repositories](https://learn.microsoft.com/en-us/graph/api/contentmanagementroot-list-repositories?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) collection | List connected repositories. |
| [Get contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-get?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) | Get one connection by its identifier. |
| [contentManagementRepository: connect](https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-connect?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) | Connect a source-control repository. |
| [contentManagementRepository: discoverAvailableRepositories](https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-discoveravailablerepositories?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.discoveredRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-discoveredrepository?view=graph-rest-beta) collection | Discover up to 200 accessible candidate repositories. |
| [contentManagementRepository: modify](https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-modify?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) | Modify a connected repository. |
| [contentManagementRepository: disconnect](https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-disconnect?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.repositoryDisconnectResult](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorydisconnectresult?view=graph-rest-beta) | Disconnect and report any cleanup warning. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentTypes | [microsoft.graph.security.contentManagement.repositoryContentType](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-contentmanagement?view=graph-rest-beta#repositorycontenttype-values) collection | Content kinds this repository is configured to deploy. The possible values are: `customDetection`, `unknownFutureValue`, `defenderWorkbook`. Use the `Prefer: include-unknown-enum-members` request header to get `defenderWorkbook`. |
| deploymentIdentity | [microsoft.graph.security.contentManagement.deploymentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-deploymentidentity?view=graph-rest-beta) | Bring-your-own deployment identity used for deployment. Optional; when omitted the platform-managed identity path is used. Provide a service principal or a managed identity. Immutable after connecting. |
| deploymentScope | [microsoft.graph.security.contentManagement.deploymentScope](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-deploymentscope?view=graph-rest-beta) | Optional Azure deployment scope, immutable after connecting the repository. |
| description | String | Optional description of the connection. |
| displayName | String | Human-readable name of the connection. Supports `$filter` \(`eq`, `ne`\) and `$orderby`. |
| id | String | A unique identifier for this resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$filter` \(`eq`, `ne`\). |
| lastDeploymentInfo | [microsoft.graph.security.contentManagement.repositoryDeploymentInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorydeploymentinfo?view=graph-rest-beta) | Status of the most recent deployment from this repository. Read-only. |
| pullRequest | [microsoft.graph.security.contentManagement.repositoryPullRequest](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorypullrequest?view=graph-rest-beta) | The setup pull request opened for this connection, when applicable. Read-only. |
| repoType | [microsoft.graph.security.contentManagement.repositoryType](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-contentmanagement?view=graph-rest-beta#repositorytype-values) | Source-control provider for this repository. Immutable after connecting. Supports `$filter` \(`eq`, `ne`\). The possible values are: `gitHub`, `azureDevOps`, `unknownFutureValue`. |
| servicePrincipal | [microsoft.graph.security.contentManagement.repositoryServicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositoryserviceprincipal?view=graph-rest-beta) | Service principal / managed identity used by the connection. Read-only. |
| sourceLocation | [microsoft.graph.security.contentManagement.repositorySettings](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorysettings?view=graph-rest-beta) | Location of the source repository \(URL and branch\). |
| systemData | [microsoft.graph.security.contentManagement.systemData](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-systemdata?view=graph-rest-beta) | Creation and last modification provenance. Read-only. |
| workloadIdentityFederation | [microsoft.graph.security.contentManagement.repositoryWorkloadIdentityFederation](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositoryworkloadidentityfederation?view=graph-rest-beta) | Workload identity federation details for the connection, when configured. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.contentManagementRepository",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "repoType": "String",
  "contentTypes": [
    "String"
  ],
  "sourceLocation": {
    "@odata.type": "microsoft.graph.security.contentManagement.repositorySettings"
  },
  "deploymentScope": {
    "@odata.type": "microsoft.graph.security.contentManagement.deploymentScope"
  },
  "deploymentIdentity": {
    "@odata.type": "microsoft.graph.security.contentManagement.deploymentIdentity"
  },
  "servicePrincipal": {
    "@odata.type": "microsoft.graph.security.contentManagement.repositoryServicePrincipal"
  },
  "workloadIdentityFederation": {
    "@odata.type": "microsoft.graph.security.contentManagement.repositoryWorkloadIdentityFederation"
  },
  "lastDeploymentInfo": {
    "@odata.type": "microsoft.graph.security.contentManagement.repositoryDeploymentInfo"
  },
  "pullRequest": {
    "@odata.type": "microsoft.graph.security.contentManagement.repositoryPullRequest"
  },
  "systemData": {
    "@odata.type": "microsoft.graph.security.contentManagement.systemData"
  }
}
```
