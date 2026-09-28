<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldvalues?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# customFieldValues resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an open collection of tenant-defined custom field values in the **customFields** property of a [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta).

## Properties

This open type has no fixed properties. To identify the available custom fields, call [List customFields](https://learn.microsoft.com/en-us/graph/api/security-casemanagement-casetypeconfiguration-list-customfields?view=graph-rest-beta) at `/security/caseManagement/caseTypeConfigurations/{caseTypeConfigurationId}/customFields`, where `{caseTypeConfigurationId}` is `genericCase` or `incidentCase`.

Important

Use the definition's **displayName**, not its **id**, as the dynamic property name. The display name must match exactly one definition in the case type configuration. A request fails if the name matches no definition or more than one definition. If a display name changes, update integrations that use it as a key.

For each custom field value:

- Use the definition's **displayName** value as the dynamic property name.
- Supply an object as the dynamic property value. Bare values such as strings or numbers aren't supported.
- Include `@odata.type` in every value object.
- Use the definition's `@odata.type` to select the corresponding custom field value type and value property from the following table.
- Use **isRequired** and **isDisabled** to determine whether the field must or can be supplied.
- For an options field, use only values listed in the definition's **options** property.

### Custom field value mapping

| Custom field definition `@odata.type` | Custom field value `@odata.type` | Value property |
| :--- | :--- | :--- |
| [`#microsoft.graph.security.caseManagement.dateTimeCustomFieldDefinition`](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-datetimecustomfielddefinition?view=graph-rest-beta) | [`#microsoft.graph.security.caseManagement.customFieldDateTimeValue`](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddatetimevalue?view=graph-rest-beta) | **valueDateTime** \(DateTimeOffset\) |
| [`#microsoft.graph.security.caseManagement.numberCustomFieldDefinition`](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-numbercustomfielddefinition?view=graph-rest-beta) | [`#microsoft.graph.security.caseManagement.customFieldNumberValue`](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldnumbervalue?view=graph-rest-beta) | **value** \(Int32\) |
| [`#microsoft.graph.security.caseManagement.optionsCustomFieldDefinition`](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-optionscustomfielddefinition?view=graph-rest-beta) | [`#microsoft.graph.security.caseManagement.customFieldOptionsValue`](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldoptionsvalue?view=graph-rest-beta) | **values** \(String collection\) |
| [`#microsoft.graph.security.caseManagement.stringCustomFieldDefinition`](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-stringcustomfielddefinition?view=graph-rest-beta) | [`#microsoft.graph.security.caseManagement.customFieldStringValue`](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldstringvalue?view=graph-rest-beta) | **value** \(String\) |

### Example

The following example shows the shape of a **customFields** payload. `External reference` is the exact **displayName** returned by the custom field definition.

```json
{
  "customFields": {
    "External reference": {
      "@odata.type": "#microsoft.graph.security.caseManagement.customFieldStringValue",
      "value": "INC-2026-0042"
    }
  }
}
```

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.customFieldValues"
}
```
