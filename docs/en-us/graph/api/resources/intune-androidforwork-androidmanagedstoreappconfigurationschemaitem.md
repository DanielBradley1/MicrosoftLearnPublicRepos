<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschemaitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidManagedStoreAppConfigurationSchemaItem resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Single configuration item inside an Android application's custom configuration schema.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| index | Int32 | Unique index the application uses to maintain nested schema items |
| parentIndex | Int32 | Index of parent schema item to track nested schema items |
| schemaItemKey | String | Unique key the application uses to identify the item |
| displayName | String | Human readable name |
| description | String | Description of what the item controls within the application |
| defaultBoolValue | Boolean | Default value for boolean type items, if specified by the app developer |
| defaultIntValue | Int32 | Default value for integer type items, if specified by the app developer |
| defaultStringValue | String | Default value for string type items, if specified by the app developer |
| defaultStringArrayValue | String collection | Default value for string array type items, if specified by the app developer |
| dataType | [androidManagedStoreAppConfigurationSchemaItemDataType](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschemaitemdatatype?view=graph-rest-beta) | The type of value this item describes. Possible values are: `bool`, `integer`, `string`, `choice`, `multiselect`, `bundle`, `bundleArray`, `hidden`. |
| selections | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-keyvaluepair?view=graph-rest-beta) collection | List of human readable name/value pairs for the valid values that can be set for this item \(Choice and Multiselect items only\) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidManagedStoreAppConfigurationSchemaItem",
  "index": 1024,
  "parentIndex": 1024,
  "schemaItemKey": "String",
  "displayName": "String",
  "description": "String",
  "defaultBoolValue": true,
  "defaultIntValue": 1024,
  "defaultStringValue": "String",
  "defaultStringArrayValue": [
    "String"
  ],
  "dataType": "String",
  "selections": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "String",
      "value": "String"
    }
  ]
}
```
