<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutresponse?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# customExtensionCalloutResponse resource type

Namespace: microsoft.graph

Defines the custom extension callout response payload that external systems send back for callback scenarios of custom extensions.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| data | [customExtensionData](https://learn.microsoft.com/en-us/graph/api/resources/customextensiondata?view=graph-rest-1.0) | Contains the data the external system provides to the custom extension endpoint. |
| source | String | Identifies the external system or event context related to the response. |
| type | String | Describes the type of event related to the response. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customExtensionCalloutResponse",
  "source": "String",
  "type": "String",
  "data": {
    "@odata.type": "microsoft.graph.customExtensionData"
  }
}
```
