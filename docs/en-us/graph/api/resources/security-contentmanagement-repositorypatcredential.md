<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorypatcredential?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# repositoryPatCredential resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Supplies a personal access token as the **accessCredential** action parameter when connecting, discovering, modifying, or disconnecting a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta). Credentials are write-only and aren't returned.

Inherits from [microsoft.graph.security.contentManagement.repositoryAccessCredential](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositoryaccesscredential?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| token | String | Personal access token. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.repositoryPatCredential",
  "token": "String"
}
```
