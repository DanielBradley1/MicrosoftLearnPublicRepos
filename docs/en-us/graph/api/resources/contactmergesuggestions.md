<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/contactmergesuggestions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# contactMergeSuggestions resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the feature to suggest merging contact items when Outlook detects duplicates in the user's contacts list.

This resource provides a means to enable or disable the feature at the user level. By default, suggestion is enabled. Duplicate contact items remain as duplicates in the contact folder unless the user selects merging them.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/contactmergesuggestions-get?view=graph-rest-beta) | [contactMergeSuggestions](https://learn.microsoft.com/en-us/graph/api/resources/contactmergesuggestions?view=graph-rest-beta) | Read the properties of a **contactMergeSuggestions** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/contactmergesuggestions-update?view=graph-rest-beta) | None | Update the properties of a **contactMergeSuggestions** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | `true` if the duplicate contact merge suggestions feature is enabled for the user; `false` if the feature is disabled. Default value is `true`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "isEnabled": "Boolean"
}
```
