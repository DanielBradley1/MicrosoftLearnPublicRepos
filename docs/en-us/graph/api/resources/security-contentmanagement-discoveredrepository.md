<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-discoveredrepository?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-12 -->

# discoveredRepository resource type

Namespace: microsoft.graph.security.contentManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an item in the **discoverAvailableRepositories** action response for a [contentManagementRepository](https://learn.microsoft.com/en-us/graph/api/resources/security-contentmanagement-contentmanagementrepository?view=graph-rest-beta), using its **accessCredential** action parameter. The result is transient and has no stable identifier.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| branches | String collection | Branch names available in the repository. |
| fullName | String | Provider full name, for example `owner/repo`. |
| url | String | Repository URL. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.contentManagement.discoveredRepository",
  "url": "String",
  "fullName": "String",
  "branches": [
    "String"
  ]
}
```
