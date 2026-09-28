<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/structureddataentry?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-09 -->

# structuredDataEntry resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a single key-value pair of [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta) objects.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| keyEntry | [structuredDataEntryTypedValue](https://learn.microsoft.com/en-us/graph/api/resources/structureddataentrytypedvalue?view=graph-rest-beta) | The key entry. |
| valueEntry | [structuredDataEntryTypedValue](https://learn.microsoft.com/en-us/graph/api/resources/structureddataentrytypedvalue?view=graph-rest-beta) | The value entry. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.structuredDataEntry",
  "keyEntry": {
    "@odata.type": "microsoft.graph.structuredDataEntryTypedValue"
  },
  "valueEntry": {
    "@odata.type": "microsoft.graph.structuredDataEntryTypedValue"
  }
}
```
