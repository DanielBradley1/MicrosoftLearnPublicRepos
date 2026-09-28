<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensionoverwriteconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-25 -->

# customExtensionOverwriteConfiguration resource type

Namespace: microsoft.graph

Configuration regarding properties of the custom extension which can be overwritten per event listener. If no values are provided, the properties on the custom extension are used.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| clientConfiguration | [customExtensionClientConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0) | Configuration regarding properties of the custom extension which can be overwritten per event listener. If no values are provided, the properties on the custom extension are used. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customExtensionOverwriteConfiguration",
  "clientConfiguration": {
    "@odata.type": "microsoft.graph.customExtensionClientConfiguration"
  }
}
```
