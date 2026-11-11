<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/sensitivecontentevidence?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-10 -->

# sensitiveContentEvidence resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an item in the **evidences** collection of [classificationGradingContentLocation](https://learn.microsoft.com/en-us/graph/api/resources/classificationgradingcontentlocation?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| length | Int32 | The length of the evidence text. |
| match | String | The matched evidence text. |
| offset | Int32 | The start position of the evidence text. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.sensitiveContentEvidence",
  "match": "String",
  "offset": "Integer",
  "length": "Integer"
}
```
