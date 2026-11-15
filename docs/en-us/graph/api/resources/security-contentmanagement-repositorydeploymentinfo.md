<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorydeploymentinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# repositoryDeploymentInfo resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the last deployment status in the **lastDeploymentInfo** property of a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta).

Deployment status requires a verified GitHub App installation. See [connect](https://learn.microsoft.com/en-us/graph/api/security-contentmanagement-contentmanagementrepository-connect?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deploymentFetchStatus | [microsoft.graph.security.contentManagement.repositoryDeploymentFetchStatus](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-contentmanagement?view=graph-rest-beta#repositorydeploymentfetchstatus-values) | Whether deployment status could be fetched. The possible values are: `success`, `unauthorized`, `notFound`, `unknownFutureValue`, `unavailable`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `unavailable`. |
| message | String | Human-readable status or error message. |
| run | [microsoft.graph.security.contentManagement.repositoryDeployment](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorydeployment?view=graph-rest-beta) | Deployment details; null when no run was fetched. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.repositoryDeploymentInfo",
  "deploymentFetchStatus": "String",
  "message": "String",
  "run": {
    "@odata.type": "microsoft.graph.security.contentManagement.repositoryDeployment"
  }
}
```
