<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/displaynamelocalization?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# displayNameLocalization resource type

Provides the ability for an administrator to customize the string used in a shared Microsoft 365 experience.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | If present, the value of this field contains the **displayName** string that has been set for the language present in the **languageTag** field. |
| languageTag | String | Provides the language culture-code and friendly name of the language that the **displayName** field has been provided in. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "displayName": "string",
  "languageTag": "string"
}
```
