<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationconfigurationvalidation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# authenticationConfigurationValidation resource type

Namespace: microsoft.graph

The validation result of a [validateAuthenticationConfiguration action](https://learn.microsoft.com/en-us/graph/api/customauthenticationextension-validateauthenticationconfiguration?view=graph-rest-1.0) that validates a [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0) configuration.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errors | [genericError](https://learn.microsoft.com/en-us/graph/api/resources/genericerror?view=graph-rest-1.0) collection | Errors in the validation result of a [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0). |
| warnings | [genericError](https://learn.microsoft.com/en-us/graph/api/resources/genericerror?view=graph-rest-1.0) collection | Warnings in the validation result of a [customAuthenticationExtension](https://learn.microsoft.com/en-us/graph/api/resources/customauthenticationextension?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationConfigurationValidation",
  "errors": [
    {
      "@odata.type": "microsoft.graph.genericError"
    }
  ],
  "warnings": [
    {
      "@odata.type": "microsoft.graph.genericError"
    }
  ]
}
```
