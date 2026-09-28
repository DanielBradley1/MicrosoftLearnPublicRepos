<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/structureddataentrytypedvalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-09 -->

# structuredDataEntryTypedValue resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the typed value for the key or value in a [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| type | structuredDataEntryValueType | The type of the value. The possible values are: `dateTime`, `boolean`, `byte`, `string`, `integer32`, `unsignedInteger32`, `integer64`, `unsignedInteger64`, `stringArray`, `byteArray`, `unknownFutureValue`. |
| values | String collection | Represents the value. The contained elements might be one of the following cases: when the **type** is `stringArray`, it contains arbitrary string values; otherwise, it contains exactly one string value. The caller is responsible for data type conversion. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.structuredDataEntryTypedValue",
  "type": "String",
  "values": ["String"]
}
```
