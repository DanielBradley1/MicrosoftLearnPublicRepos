<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainercustompropertyvalue?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-25 -->

# fileStorageContainerCustomPropertyValue resource type

Namespace: microsoft.graph

Contains the custom property values stored in a [fileStorageContainerCustomPropertyDictionary](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainercustompropertydictionary?view=graph-rest-1.0) resource.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isSearchable | Boolean | Indicates whether the custom property is searchable. Optional. The default value is `false`. |
| value | String | Value of the custom property. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.fileStorageContainerCustomPropertyValue",
  "value": "String",
  "isSearchable": "Boolean"
}
```
