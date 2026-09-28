<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/regionalandlanguagesettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# regionalAndLanguageSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An open type that represents a user's preferences for languages in various contexts, and for regional locale and formatting that drives the default calendar, and formatting for date and time.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/regionalandlanguagesettings-get?view=graph-rest-beta) | [regionalAndLanguageSettings](https://learn.microsoft.com/en-us/graph/api/resources/regionalandlanguagesettings?view=graph-rest-beta) | Read properties of a **regionalAndLanguageSettings** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/regionalandlanguagesettings-update?view=graph-rest-beta) | [regionalAndLanguageSettings](https://learn.microsoft.com/en-us/graph/api/resources/regionalandlanguagesettings?view=graph-rest-beta) | Update all or a subset of the properties of the **regionalAndLanguageSettings** object for a user. |

## Properties

| Property | Type | Description |
| --- | --- | --- |
| defaultDisplayLanguage | [localeInfo](https://learn.microsoft.com/en-us/graph/api/resources/localeinfo?view=graph-rest-beta) | The user's preferred user interface language \(menus, buttons, ribbons, warning messages\) for Microsoft web applications.  <br>  <br>Returned by default. Not nullable. |
| authoringLanguages | [localeInfo](https://learn.microsoft.com/en-us/graph/api/resources/localeinfo?view=graph-rest-beta) collection | Prioritized list of languages the user reads and authors in.  <br>  <br>Returned by default. Not nullable. |
| defaultTranslationLanguage | [localeInfo](https://learn.microsoft.com/en-us/graph/api/resources/localeinfo?view=graph-rest-beta) | The language a user expects to have documents, emails, and messages translated into.  <br>  <br>Returned by default. |
| defaultSpeechInputLanguage | [localeInfo](https://learn.microsoft.com/en-us/graph/api/resources/localeinfo?view=graph-rest-beta) | The language a user expected to use as input for text to speech scenarios.  <br>  <br>Returned by default. |
| defaultRegionalFormat | [localeInfo](https://learn.microsoft.com/en-us/graph/api/resources/localeinfo?view=graph-rest-beta) | The locale that drives the default date, time, and calendar formatting.  <br>  <br>Returned by default. |
| regionalFormatOverrides | [regionalFormatOverrides](https://learn.microsoft.com/en-us/graph/api/resources/regionalformatoverrides?view=graph-rest-beta) | Allows a user to override their defaultRegionalFormat with field specific formats.  <br>  <br>Returned by default. |
| translationPreferences | [translationPreferences](https://learn.microsoft.com/en-us/graph/api/resources/translationpreferences?view=graph-rest-beta) | The user's preferred settings when consuming translated documents, emails, messages, and websites.  <br>  <br>Returned by default. Not nullable. |

## Relationships

None.

## JSON representation

The following is a JSON definition of the resource.

```json
{
    "defaultDisplayLanguage": {"@odata.type":"microsoft.graph.localeInfo"},
    "authoringLanguages": [{"@odata.type":"microsoft.graph.localeInfo"}],
    "defaultTranslationLanguage": {"@odata.type":"microsoft.graph.localeInfo"},
    "defaultSpeechInputLanguage": {"@odata.type":"microsoft.graph.localeInfo"},
    "defaultRegionalFormat": {"@odata.type":"microsoft.graph.localeInfo"},
    "regionalFormatOverrides": {"@odata.type":"microsoft.graph.regionalFormatOverrides"},
    "translationPreferences":{"@odata.type":"microsoft.graph.translationPreferences"}
}
```
