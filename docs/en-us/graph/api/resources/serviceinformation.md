<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/serviceinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# serviceInformation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents basic descriptive data about cloud services that a user has chosen to refer to from their account.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The name of the cloud service \(for example, Twitter, Instagram\). |
| webUrl | String | Contains the URL for the service being referenced. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "name": "String",
  "webUrl": "String"
}
```
