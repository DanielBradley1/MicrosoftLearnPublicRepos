<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contentmanagementroot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# contentManagementRoot resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides the entry point under `/security` for content repositories, the published security content catalog, and the tenant's installed content.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List installedPackageContents](https://learn.microsoft.com/en-us/graph/api/contentmanagementroot-list-installedpackagecontents?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.installedContentItem](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-installedcontentitem?view=graph-rest-beta) collection | List installed content items across all installed packages. |
| [List installedPackages](https://learn.microsoft.com/en-us/graph/api/contentmanagementroot-list-installedpackages?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.installedPackage](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-installedpackage?view=graph-rest-beta) collection | List the content packages installed in the tenant. |
| [List packageContents](https://learn.microsoft.com/en-us/graph/api/contentmanagementroot-list-packagecontents?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.contentItem](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentitem?view=graph-rest-beta) collection | List published content items across all catalog packages. |
| [List packages](https://learn.microsoft.com/en-us/graph/api/contentmanagementroot-list-packages?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.contentPackage](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentpackage?view=graph-rest-beta) collection | List content packages published in the catalog. |
| [List repositories](https://learn.microsoft.com/en-us/graph/api/contentmanagementroot-list-repositories?view=graph-rest-beta) | [microsoft.graph.security.contentManagement.contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) collection | Get the source-control repositories connected to the tenant. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | A unique identifier for this resource. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| installedPackageContents | [microsoft.graph.security.contentManagement.installedContentItem](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-installedcontentitem?view=graph-rest-beta) collection | Installed content items listed across every installed package. |
| installedPackages | [microsoft.graph.security.contentManagement.installedPackage](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-installedpackage?view=graph-rest-beta) collection | Content packages the tenant has installed, keyed the same way as **packages** so the same identity addresses the catalog entry and the tenant's installation of it. |
| packageContents | [microsoft.graph.security.contentManagement.contentItem](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentitem?view=graph-rest-beta) collection | Read-only content items published across packages for cross-package discovery. |
| packages | [microsoft.graph.security.contentManagement.contentPackage](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentpackage?view=graph-rest-beta) collection | Content packages published in the catalog and available to install. Read-only. |
| repositories | [microsoft.graph.security.contentManagement.contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta) collection | Connected source-control repositories that deliver security content as code. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.contentManagementRoot",
  "id": "String (identifier)"
}
```
