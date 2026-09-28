<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/translationlanguageoverride?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# translationLanguageOverride resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents any translation override for a language.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| languageTag | String | The language to apply the override.  <br>  <br>Returned by default. Not nullable. |
| translationBehavior | [translationBehavior](https://learn.microsoft.com/en-us/graph/api/resources/translationpreferences?view=graph-rest-beta#translationbehavior-values) | The translation override behavior for the language, if any.  <br>  <br>Returned by default. Not nullable. |

## Relationships

None.

## JSON representation

The following is a JSON definition of the resource.

```json
{
    "languageTag": "string",
    "translationBehavior": "string"
}
```
