<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionwebcategorydestination?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-09 -->

# tlsInspectionWebCategoryDestination resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a collection of web category destinations in a [TLS inspection rule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectionrule?view=graph-rest-beta) for applying TLS inspection based on predefined web content categories.

Inherits from [microsoft.graph.networkaccess.tlsInspectionDestination](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-tlsinspectiondestination?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| values | String collection | A collection of web category names to match against. This collection cannot be empty or null. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.tlsInspectionWebCategoryDestination",
  "values": [
    "String"
  ]
}
```
