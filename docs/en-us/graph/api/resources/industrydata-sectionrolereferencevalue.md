<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-sectionrolereferencevalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# sectionRoleReferenceValue resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A reference value for a role in a section.

Inherits from [microsoft.graph.industryData.referenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencevalue?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | Inherited from [microsoft.graph.industryData.referenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencevalue?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| value | [microsoft.graph.industryData.referenceDefinition](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencedefinition?view=graph-rest-beta) | Inherited from [microsoft.graph.industryData.referenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-referencevalue?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.sectionRoleReferenceValue",
  "code": "String"
}
```
