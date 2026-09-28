<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschema?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# androidForWorkAppConfigurationSchema resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Schema describing an Android for Work application's custom configurations.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List androidForWorkAppConfigurationSchemas](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkappconfigurationschema-list?view=graph-rest-beta) | [androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschema?view=graph-rest-beta) collection | List properties and relationships of the [androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschema?view=graph-rest-beta) objects. |
| [Get androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkappconfigurationschema-get?view=graph-rest-beta) | [androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschema?view=graph-rest-beta) | Read properties and relationships of the [androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschema?view=graph-rest-beta) object. |
| [Create androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkappconfigurationschema-create?view=graph-rest-beta) | [androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschema?view=graph-rest-beta) | Create a new [androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschema?view=graph-rest-beta) object. |
| [Delete androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkappconfigurationschema-delete?view=graph-rest-beta) | None | Deletes a [androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschema?view=graph-rest-beta). |
| [Update androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/intune-androidforwork-androidforworkappconfigurationschema-update?view=graph-rest-beta) | [androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschema?view=graph-rest-beta) | Update the properties of a [androidForWorkAppConfigurationSchema](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschema?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity the Android package name for the application the schema corresponds to |
| exampleJson | Binary | UTF8 encoded byte array containing example JSON string conforming to this schema that demonstrates how to set the configuration for this app |
| schemaItems | [androidForWorkAppConfigurationSchemaItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-androidforworkappconfigurationschemaitem?view=graph-rest-beta) collection | Collection of items each representing a named configuration option in the schema |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.androidForWorkAppConfigurationSchema",
  "id": "String (identifier)",
  "exampleJson": "binary",
  "schemaItems": [
    {
      "@odata.type": "microsoft.graph.androidForWorkAppConfigurationSchemaItem",
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
