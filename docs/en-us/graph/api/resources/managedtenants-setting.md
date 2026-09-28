<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-setting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# setting resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a setting that is used within a baseline.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name for the setting. Required. Read-only. |
| jsonValue | String | The value for the setting serialized as string of JSON. Required. Read-only. |
| overwriteAllowed | Boolean | A flag indicating whether the setting can be override existing configurations when applied. Required. Read-only. |
| valueType | managementParameterValueType | The data type for the setting. The possible values are: `string`, `integer`, `boolean`, `guid`, `stringCollection`, `integerCollection`, `booleanCollection`, `guidCollection`, `unknownFutureValue`. Required. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.managedTenants.setting",
  "displayName": "String",
  "overwriteAllowed": "Boolean",
  "valueType": "String",
  "jsonValue": "String"
}
```
