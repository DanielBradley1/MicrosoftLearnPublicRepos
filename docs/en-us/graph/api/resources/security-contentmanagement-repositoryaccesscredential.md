<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositoryaccesscredential?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# repositoryAccessCredential resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the write-only **accessCredential** action parameter used to connect, discover, modify, or disconnect a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta). This type is abstract and cannot be instantiated directly. Use a [repositoryOAuthCredential](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositoryoauthcredential?view=graph-rest-beta) or [repositoryPatCredential](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-repositorypatcredential?view=graph-rest-beta) and distinguish derived types with `@odata.type`. This is an abstract type.

## Methods

None.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.repositoryAccessCredential"
}
```
