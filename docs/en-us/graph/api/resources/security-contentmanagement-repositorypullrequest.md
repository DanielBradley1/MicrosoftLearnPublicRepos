<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorypullrequest?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# repositoryPullRequest resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the setup pull request in the **pullRequest** property of a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| state | [microsoft.graph.security.contentManagement.repositoryPullRequestState](https://learn.microsoft.com/en-us/graph/api/resources/enums-security-contentmanagement?view=graph-rest-beta#repositorypullrequeststate-values) | Whether the pull request is open, closed, or merged. The possible values are: `open`, `closed`, `unknownFutureValue`, `merged`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `merged`. |
| url | String | Pull request URL. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.repositoryPullRequest",
  "url": "String",
  "state": "String"
}
```
