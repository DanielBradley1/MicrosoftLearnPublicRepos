<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappuser?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-11-19 -->

# discoveredCloudAppUser resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user who accessed a discovered cloud app.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-discoveredcloudappdetail-list-users?view=graph-rest-beta) | [microsoft.graph.security.discoveredCloudAppUser](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappuser?view=graph-rest-beta) collection | Get a list of [users](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappuser?view=graph-rest-beta) who accessed a discovered cloud app. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| userIdentifier | String | The identifier of a user who accessed the discovered cloud app. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.discoveredCloudAppUser",
  "userIdentifier": "String"
}
```
