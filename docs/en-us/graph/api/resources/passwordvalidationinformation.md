<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/passwordvalidationinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# passwordValidationInformation resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Exposes the properties that specify whether a user's password is valid, when validated against the tenant's password validation policy. This resource also returns the list of rules against which the password was validated and whether the user's password passed those roles.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isValid | Boolean | Specifies whether the password is valid based on the calculation of the results in the **validationResults** property. Not nullable. Read-only. |
| validationResults | [validationResult](https://learn.microsoft.com/en-us/graph/api/resources/validationresult?view=graph-rest-beta) collection | The list of password validation rules and whether the password passed those rules. Not nullable. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.passwordValidationInformation",
  "isValid": "Boolean",
  "validationResults": [
    {
      "@odata.type": "microsoft.graph.validationResult"
    }
  ]
}
```
