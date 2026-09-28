<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/validationresult?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# validationResult resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Exposes the properties that specify the rules against which a user's password was validated, and the validation results.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| message | String | The string containing the reason for why the rule passed or not. Read-only. Not nullable. |
| ruleName | String | The string containing the name of the password validation rule that the action was validated against. Read-only. Not nullable. |
| validationPassed | Boolean | Whether the password passed or failed the validation rule. Read-only. Not nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.validationResult",
  "ruleName": "String",
  "validationPassed": "Boolean",
  "message": "String"
}
```
