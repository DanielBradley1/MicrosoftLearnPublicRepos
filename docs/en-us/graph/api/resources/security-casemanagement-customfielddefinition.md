<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-31 -->

# customFieldDefinition resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Abstract base type describing a single tenant-defined custom field — one entry in the blank-form schema of a [caseTypeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casetypeconfiguration?view=graph-rest-beta). Each custom field is a concrete subtype, identified by `@odata.type`, that marks the field kind.

This is an abstract type and can't be instantiated directly. Collections of custom-field definitions contain instances of the following derived types:

- [stringCustomFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-stringcustomfielddefinition?view=graph-rest-beta)
- [numberCustomFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-numbercustomfielddefinition?view=graph-rest-beta)
- [dateTimeCustomFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-datetimecustomfielddefinition?view=graph-rest-beta)
- [optionsCustomFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-optionscustomfielddefinition?view=graph-rest-beta)

Custom-field definitions are reached by containment navigation from a case type configuration at `/security/caseManagement/caseTypeConfigurations/{caseTypeConfigurationId}/customFields`, so each field is individually addressable. The collection is read-only.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-customfields?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta) collection | Get a list of the [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta) objects for a case type. |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-customfielddefinition-get?view=graph-rest-beta) | [microsoft.graph.security.caseManagement.customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta) | Read the properties of a [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The field description. Supports `$filter` and `$orderby`. |
| displayName | String | The field label shown on the case form. Supports `$filter` and `$orderby`. |
| id | String | The unique identifier of the custom field. Read-only. Supports `$filter` and `$orderby`. |
| isDisabled | Boolean | `true` if the field is disabled; otherwise, `false`. Supports `$filter` and `$orderby`. |
| isRequired | Boolean | `true` if a value is required for this field; otherwise, `false`. Supports `$filter` and `$orderby`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.customFieldDefinition",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "isRequired": "Boolean",
  "isDisabled": "Boolean"
}
```
