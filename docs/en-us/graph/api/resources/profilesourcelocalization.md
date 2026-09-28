<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/profilesourcelocalization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-12 -->

# profileSourceLocalization resource type

Namespace: microsoft.graph

Represents configurations that allow an administrator to customize the appearance of the **displayName** and **webUrl** properties in a profile source. The administrator can define a default display name and web URL, along with a set of alternative translations for the languages supported in their organization.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Localized display name. |
| languageTag | String | Language locale. |
| webUrl | String | Localized profile source URL. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.profileSourceLocalization",
  "displayName": "String",
  "languageTag": "String",
  "webUrl": "String"
}
```
