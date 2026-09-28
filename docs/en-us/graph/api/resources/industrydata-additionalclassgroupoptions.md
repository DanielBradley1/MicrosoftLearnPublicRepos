<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/industrydata-additionalclassgroupoptions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# additionalClassGroupOptions resource type

Namespace: microsoft.graph.industryData

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The different management choices for the class groups to be provisioned.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createTeam | Boolean | Indicates whether a team should be created for the class group. |
| writeDisplayNameOnCreateOnly | Boolean | Indicates whether the class group display name should be set on create. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.industryData.additionalClassGroupOptions",
  "createTeam": "Boolean",
  "writeDisplayNameOnCreateOnly": "Boolean"
}
```
