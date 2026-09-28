<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-datetimecustomfielddefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-31 -->

# dateTimeCustomFieldDefinition resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the schema for a date/time custom field on a case form.

Inherits from [microsoft.graph.security.caseManagement.customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). Instances appear in the custom-fields collection of a [caseTypeConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-casetypeconfiguration?view=graph-rest-beta), differentiated by the `@odata.type` value `#microsoft.graph.security.caseManagement.dateTimeCustomFieldDefinition`.

## Methods

For methods, see the base type [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultDateTime | DateTimeOffset | The default date/time value applied to the field on a new case. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| description | String | The field description. Inherited from [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). |
| displayName | String | The field label shown on the case form. Inherited from [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). |
| id | String | The unique identifier of the custom field. Read-only. Inherited from [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). |
| isDisabled | Boolean | `true` if the field is disabled; otherwise, `false`. Inherited from [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). |
| isRequired | Boolean | `true` if a value is required for this field; otherwise, `false`. Inherited from [customFieldDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddefinition?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.dateTimeCustomFieldDefinition",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "isRequired": "Boolean",
  "isDisabled": "Boolean",
  "defaultDateTime": "String (timestamp)"
}
```
