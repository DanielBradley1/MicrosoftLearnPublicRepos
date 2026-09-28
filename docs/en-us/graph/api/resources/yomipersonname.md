<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/yomipersonname?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# yomiPersonName resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Provides a mechanism for a user to store information about how to pronounce a name for non-native speakers of the language that the [personName](https://learn.microsoft.com/en-us/graph/api/resources/personname?view=graph-rest-beta) resource is represented in.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Composite of first and last name pronunciation guides. |
| first | String | Pronunciation guide for the first name of the user. |
| last | String | Pronunciation guide for the last name of the user. |
| maiden | String | Pronunciation guide for the maiden name of the user. |
| middle | String | Pronunciation guide for the middle name of the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json

{
  "displayName": "String",
  "first": "String",
  "maiden": "String",
  "middle": "String",
  "last": "String"
}
```
