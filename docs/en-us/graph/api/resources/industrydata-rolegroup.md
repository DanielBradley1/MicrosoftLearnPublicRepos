<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolegroup?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# roleGroup resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a named collection of individual roles.

Transformation of the data is often shaped by each individual user's role within an organization. These roles are defined as reference definitions. Given the number of potential roles, binding each role individually would result in a tedious user experience. Role groups are simply a collection of role values that provides a convenient way to reference multiple reference definitions. The default role groups are `Students` and `Staff`.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/industrydata-rolegroup-list?view=graph-rest-beta) | [microsoft.graph.industryData.roleGroup](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolegroup?view=graph-rest-beta) collection | Get a list of the [roleGroup](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolegroup?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/industrydata-rolegroup-get?view=graph-rest-beta) | [microsoft.graph.industryData.roleGroup](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolegroup?view=graph-rest-beta) | Read the properties and relationships of a [roleGroup](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolegroup?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The name of the role group. |
| roles | [microsoft.graph.industryData.roleReferenceValue](https://learn.microsoft.com/en-us/graph/api/resources/industrydata-rolereferencevalue?view=graph-rest-beta) collection | The set of roles included in the role group. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.roleGroup",
  "displayName": "String",
  "roles": [
    {
      "@odata.type": "microsoft.graph.industryData.roleReferenceValue"
    }
  ]
}
```
