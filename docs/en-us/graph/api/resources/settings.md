<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/settings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# settings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the current required settings for a user to use the analytics API.

For the analytics API to return results for users, they must have a cloud-hosted mailbox that’s enabled for Microsoft Graph, have a valid MyAnalytics license, and be opted in to using MyAnalytics.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get settings](https://learn.microsoft.com/en-us/graph/api/useranalytics-get-settings?view=graph-rest-beta) | [settings](https://learn.microsoft.com/en-us/graph/api/resources/settings?view=graph-rest-beta) | Get the following property settings for a user. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hasGraphMailbox | Boolean | Specifies if the user's primary mailbox is hosted in the cloud and is enabled for Microsoft Graph. |
| hasLicense | Boolean | Specifies if the user has a MyAnalytics license assigned. |
| hasOptedOut | Boolean | Specifies if the user opted out of MyAnalytics. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "hasGraphMailbox": "Boolean",
  "hasLicense": "Boolean",
  "hasOptedOut": "Boolean"
}
```
