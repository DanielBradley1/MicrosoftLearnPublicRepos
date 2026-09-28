<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationlocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-04 -->

# applicationLocation resource type

Namespace: microsoft.graph

Represents the location attributes of an application, used to indicate where its infrastructure operates and where the owning organization is based. The **location** property of the [applicationRiskFactorGeneralInfo](https://learn.microsoft.com/en-us/graph/api/resources/applicationriskfactorgeneralinfo?view=graph-rest-1.0) resource is an **applicationLocation** object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dataCenter | String | Specifies the region or physical location where the application's primary data center is hosted. |
| headquarters | String | Specifies the city, country or region where the application's owning organization is headquartered. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.applicationLocation",
  "dataCenter": "String",
  "headquarters": "String"
}
```
