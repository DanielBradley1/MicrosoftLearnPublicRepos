<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/bucketcapability?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# bucketCapability resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **capabilities** property of the [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta) resource uses this type.

Server-computed, read-only capability flags indicating which optional features are enabled for a [bucket](https://learn.microsoft.com/en-us/graph/api/resources/bucket?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| extensions | Boolean | Indicates whether custom extension fields are enabled for the bucket. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.bucketCapability",
  "extensions": "Boolean"
}
```
