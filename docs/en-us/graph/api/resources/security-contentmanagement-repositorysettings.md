<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorysettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# repositorySettings resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains the URL and branch in the **sourceLocation** property of a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta); the **deploymentLogsUrl** is read-only.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| branch | String | Branch that content is deployed from. |
| deploymentLogsUrl | String | URL where deployment logs can be viewed. Read-only. |
| displayUrl | String | Human-friendly display URL. |
| url | String | Repository URL. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.repositorySettings",
  "url": "String",
  "displayUrl": "String",
  "branch": "String",
  "deploymentLogsUrl": "String"
}
```
