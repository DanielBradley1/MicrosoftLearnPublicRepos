<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencevalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# referenceValue resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents a pointer to an entry in the [referenceDefinitions](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) collection with a specific reference type.

Base type of [identifierTypeReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-identifiertypereferencevalue?view=graph-rest-beta), [roleReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolereferencevalue?view=graph-rest-beta), [userMatchTargetReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-usermatchtargetreferencevalue?view=graph-rest-beta), and [yearReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-yearreferencevalue?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The code of the desired **referenceDefinition** entry. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| value | [microsoft.graph.industryData.referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) | Reference to the bound **referenceDefinition** entity. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.referenceValue",
  "code": "String"
}
```
