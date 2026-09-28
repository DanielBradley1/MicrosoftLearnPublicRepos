<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschema?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidManagedStoreAppConfigurationSchema resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Schema describing an Android application's custom configurations.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidManagedStoreAppConfigurationSchemas](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreappconfigurationschema-list?view=graph-rest-beta) | [androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschema?view=graph-rest-beta) collection | List properties and relationships of the [androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschema?view=graph-rest-beta) objects. |
| [Get androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreappconfigurationschema-get?view=graph-rest-beta) | [androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschema?view=graph-rest-beta) | Read properties and relationships of the [androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschema?view=graph-rest-beta) object. |
| [Create androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreappconfigurationschema-create?view=graph-rest-beta) | [androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschema?view=graph-rest-beta) | Create a new [androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschema?view=graph-rest-beta) object. |
| [Delete androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreappconfigurationschema-delete?view=graph-rest-beta) | None | Deletes a [androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschema?view=graph-rest-beta). |
| [Update androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidmanagedstoreappconfigurationschema-update?view=graph-rest-beta) | [androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschema?view=graph-rest-beta) | Update the properties of a [androidManagedStoreAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschema?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity the Android package name for the application the schema corresponds to |
| exampleJson | Binary | UTF8 encoded byte array containing example JSON string conforming to this schema that demonstrates how to set the configuration for this app |
| schemaItems | [androidManagedStoreAppConfigurationSchemaItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschemaitem?view=graph-rest-beta) collection | Collection of items each representing a named configuration option in the schema. It only contains the root-level configuration. |
| nestedSchemaItems | [androidManagedStoreAppConfigurationSchemaItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidmanagedstoreappconfigurationschemaitem?view=graph-rest-beta) collection | Collection of items each representing a named configuration option in the schema. It contains a flat list of all configuration. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidManagedStoreAppConfigurationSchema",
  "id": "String (identifier)",
  "exampleJson": "binary",
  "schemaItems": [
    {
      "@odata.type": "microsoft.graph.androidManagedStoreAppConfigurationSchemaItem",
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
  ],
  "nestedSchemaItems": [
    {
      "@odata.type": "microsoft.graph.androidManagedStoreAppConfigurationSchemaItem",
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
  ]
}
```
