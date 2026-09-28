<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-fileformatreferencevalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-05 -->

# fileFormatReferenceValue resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a reference to a `RefFileFormat` entry in a collection of [referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) objects.

Inherits from [referenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencevalue?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The code of the desired [referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) entry. Inherited from [referenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencevalue?view=graph-rest-beta).The possible values are: `schoolDataSyncV1`, `schoolDataSyncV2Rev1` |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| value | [microsoft.graph.industryData.referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) | The reference to the bound **referenceDefinition** entity. Inherited from [referenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencevalue?view=graph-rest-beta) |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.fileFormatReferenceValue",
  "code": "String"
}
```
