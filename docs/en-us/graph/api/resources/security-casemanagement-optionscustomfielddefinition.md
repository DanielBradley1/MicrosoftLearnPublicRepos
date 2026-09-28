<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-optionscustomfielddefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-31 -->

# optionsCustomFieldDefinition resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the schema for a single-select or multi-select custom field on a case form.

Inherits from [microsoft.graph.security.caseManagement.customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). Instances appear in the custom-fields collection of a [caseTypeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casetypeconfiguration?view=graph-rest-beta), differentiated by the `@odata.type` value `#microsoft.graph.security.caseManagement.optionsCustomFieldDefinition`. The **options** property lists the allowed values, and **defaultValues** lists the value or values selected by default.

## Methods

For methods, see the base type [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultValues | String collection | The option value or values selected by default on a new case. |
| description | String | The field description. Inherited from [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). |
| displayName | String | The field label shown on the case form. Inherited from [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). |
| id | String | The unique identifier of the custom field. Read-only. Inherited from [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). |
| isDisabled | Boolean | `true` if the field is disabled; otherwise, `false`. Inherited from [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). |
| isRequired | Boolean | `true` if a value is required for this field; otherwise, `false`. Inherited from [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). |
| options | String collection | The allowed option values a case author can choose from. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.optionsCustomFieldDefinition",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "isRequired": "Boolean",
  "isDisabled": "Boolean",
  "options": ["String"],
  "defaultValues": ["String"]
}
```
