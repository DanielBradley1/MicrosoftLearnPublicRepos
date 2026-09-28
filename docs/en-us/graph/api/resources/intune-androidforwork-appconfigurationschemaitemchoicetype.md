<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-appconfigurationschemaitemchoicetype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-10 -->

# appConfigurationSchemaItemChoiceType resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Choice configuration item inside an Android application's custom configuration schema.

Inherits from [appConfigurationSchemaItemType](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-appconfigurationschemaitemtype?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| index | Int32 | Unique index the application uses to maintain nested schema items. Valid values 0 to 2147483647 Inherited from [appConfigurationSchemaItemType](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-appconfigurationschemaitemtype?view=graph-rest-beta) |
| parentIndex | Int32 | Index of parent schema item to track nested schema items. Valid values 0 to 2147483647 Inherited from [appConfigurationSchemaItemType](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-appconfigurationschemaitemtype?view=graph-rest-beta) |
| schemaItemKey | String | Unique key the application uses to identify the item Inherited from [appConfigurationSchemaItemType](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-appconfigurationschemaitemtype?view=graph-rest-beta) |
| displayName | String | Human readable name Inherited from [appConfigurationSchemaItemType](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-appconfigurationschemaitemtype?view=graph-rest-beta) |
| description | String | Description of what the item controls within the application Inherited from [appConfigurationSchemaItemType](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-appconfigurationschemaitemtype?view=graph-rest-beta) |
| defaultValue | String | Default value, if specified by the app developer |
| selections | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidforwork-keyvaluepair?view=graph-rest-beta) collection | List of human readable name/value pairs for the valid values that can be set for this item |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.appConfigurationSchemaItemChoiceType",
  "index": 1024,
  "parentIndex": 1024,
  "schemaItemKey": "String",
  "displayName": "String",
  "description": "String",
  "defaultValue": "String",
  "selections": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "String",
      "value": "String"
    }
  ]
}
```
