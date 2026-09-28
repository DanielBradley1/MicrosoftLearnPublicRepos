<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensioncalloutrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# customExtensionCalloutRequest resource type

Namespace: microsoft.graph

Defines the custom extension callout request payload that's sent to external systems.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| data | [customExtensionData](https://learn.microsoft.com/en-us/graph/api/resources/customextensiondata?view=graph-rest-1.0) | Contains the data that will be provided to the external system. |
| source | String | Identifies the source system or event context related to the callout request. |
| type | String | Describes the type of event related to the callout request. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customExtensionCalloutRequest",
  "source": "String",
  "type": "String",
  "data": {
    "@odata.type": "microsoft.graph.customExtensionData"
  }
}
```
