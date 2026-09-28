<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/profilecardannotation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# profileCardAnnotation resource type

Allows an administrator to customize the appearance of selected fields in a Microsoft 365 profile card. The administrator can define a default display name String and a set of alternative translations for the languages supported in their organization.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | If present, the value of this field is used by the profile card as the default property label in the experience \(for example, "Cost Center"\). |
| localizations | [displayNameLocalization](https://learn.microsoft.com/en-us/graph/api/resources/displaynamelocalization?view=graph-rest-1.0) collection | Each resource in this collection represents the localized value of the attribute name for a given language, used as the default label for that locale. For example, a user with a `nb-NO` client gets "Kostnadssenter" as the attribute label, rather than "Cost Center." |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "String",
  "localizations": [{ "@odata.type": "microsoft.graph.displayNameLocalization" }]
}
```
