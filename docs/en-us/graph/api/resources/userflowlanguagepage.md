<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguagepage?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# userFlowLanguagePage resource type

Namespace: microsoft.graph

Determines the user flow language pages that are shown to users during a user flow. These language pages include both the default language translations provided by Microsoft, or custom pages that can be created to customize the language translations.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/userflowlanguagepage-get?view=graph-rest-1.0) | [userFlowLanguagePage](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguagepage?view=graph-rest-1.0) | Retrieve the values of a default or custom [userFlowLanguagePage](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguagepage?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/userflowlanguagepage-put?view=graph-rest-1.0) | [userFlowLanguagePage](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguagepage?view=graph-rest-1.0) | Update the values in a custom [userFlowLanguagePage](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguagepage?view=graph-rest-1.0) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/userflowlanguagepage-delete?view=graph-rest-1.0) | None | Deletes the values from a custom [userFlowLanguagePage](https://learn.microsoft.com/en-us/graph/api/resources/userflowlanguagepage?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The identifier of the userFlowLanguage page. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userFlowLanguagePage",
  "id": "String (identifier)"
}
```
