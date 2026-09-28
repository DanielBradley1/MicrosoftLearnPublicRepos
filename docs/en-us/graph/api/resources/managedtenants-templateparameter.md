<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-templateparameter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# templateParameter resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a parameter utilized in a management template.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | The description for the template parameter. Optional. Read-only. |
| displayName | String | The display name for the template parameter. Required. Read-only. |
| jsonAllowedValues | String | The allowed values for the template parameter represented by a serialized string of JSON. Optional. Read-only. |
| jsonDefaultValue | String | The default value for the template parameter represented by a serialized string of JSON. Required. Read-only. |
| valueType | managementParameterValueType | The data type for the template parameter.. The possible values are: `string`, `integer`, `boolean`, `guid`, `stringCollection`, `integerCollection`, `booleanCollection`, `guidCollection`, `unknownFutureValue`. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.templateParameter",
  "displayName": "String",
  "description": "String",
  "valueType": "String",
  "jsonDefaultValue": "String",
  "jsonAllowedValues": "String"
}
```
