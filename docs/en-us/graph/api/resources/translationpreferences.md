<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/translationpreferences?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# translationPreferences resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an entry in a user's translation language override list.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| translationBehavior | [translationBehavior](#translationbehavior-values) | The user's preferred translation behavior.  <br>  <br>Returned by default. Not nullable. |
| languageOverrides | [translationLanguageOverride](https://learn.microsoft.com/en-us/graph/api/resources/translationlanguageoverride?view=graph-rest-beta) collection | Translation override behavior for languages, if any.  <br>  <br>Returned by default. |
| untranslatedLanguages | String collection | The list of languages the user does not need translated. This is computed from the **authoringLanguages** collection in [regionalAndLanguageSettings](https://learn.microsoft.com/en-us/graph/api/resources/regionalandlanguagesettings?view=graph-rest-beta), and the **languageOverrides** collection in **translationPreferences**. The list specifies neutral culture values that include the language code without any country or region association. For example, it would specify "fr" for the neutral French culture, but not "fr-FR" for the French culture in France.  <br>  <br>Returned by default. Read-only. |

### translationBehavior values

| Member | Description |
| --- | --- |
| Ask | Prompt the user before translating the messages/chats/web pages for the user. |
| Yes | Automatically translate the messages/chats/web pages for the user. |
| No | Do not offer prompted or automatic translation for the user. |

## Relationships

None.

## JSON representation

The following is a JSON definition of the resource.

```json
{
    "translationBehavior": "string",
    "languageOverrides": [{"@odata.type":"microsoft.graph.translationLanguageOverride"}],
    "untranslatedLanguages": ["string"]
}
```
