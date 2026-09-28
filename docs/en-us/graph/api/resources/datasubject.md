<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/datasubject?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# dataSubject resource type

Namespace: microsoft.graph

Contains information related to the subject of a content search. This resource is an open type that allows additional properties beyond those documented here.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| email | String | Email of the data subject. |
| firstName | String | First name of the data subject. |
| lastName | String | Last Name of the data subject. |
| residency | String | The country/region of residency. The residency information is uesed only for internal reporting but not for the content search. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.dataSubject",
  "email": "String",
  "firstName": "String",
  "lastName": "String",
  "residency": "String"
}
```
