<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorydeployment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# repositoryDeployment resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the deployment run in the **run** property of a [repositoryDeploymentInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorydeploymentinfo?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deploymentDateTime | DateTimeOffset | When the deployment ran. |
| deploymentId | String | Deployment id. |
| deploymentLogsUrl | String | URL where the deployment logs can be viewed. |
| deploymentResult | [microsoft.graph.security.contentManagement.repositoryDeploymentResult](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-contentmanagement?view=graph-rest-beta#repositorydeploymentresult-values) | Result of the deployment; pending until a final result is known. The possible values are: `success`, `canceled`, `failed`, `unknownFutureValue`, `pending`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `pending`. |
| deploymentState | [microsoft.graph.security.contentManagement.repositoryDeploymentState](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-contentmanagement?view=graph-rest-beta#repositorydeploymentstate-values) | Current state of the deployment. The possible values are: `inProgress`, `completed`, `queued`, `canceling`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.repositoryDeployment",
  "deploymentId": "String",
  "deploymentState": "String",
  "deploymentResult": "String",
  "deploymentDateTime": "String (timestamp)",
  "deploymentLogsUrl": "String"
}
```
