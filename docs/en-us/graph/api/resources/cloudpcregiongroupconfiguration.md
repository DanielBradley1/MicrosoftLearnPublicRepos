<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcregiongroupconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# cloudPcRegionGroupConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a region group configuration for the Microsoft-hosted network.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| regionGroup | [cloudPcRegionGroup](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcregiongroup?view=graph-rest-beta) | The logical geographic group this region belongs to. The possible values are: `default`, `australia`, `canada`, `usCentral`, `usEast`, `usWest`, `france`, `germany`, `europeUnion`, `unitedKingdom`, `japan`, `asia`, `india`, `southAmerica`, `euap`, `usGovernment`, `usGovernmentDOD`, `unknownFutureValue`, `norway`, `switzerland`, `southKorea`, `middleEast`, `mexico`, `australasia`, `europe`, `singapore`, `hongKong`, `ireland`, `sweden`, `poland`, `italy`, `spain`, `netherlands`, `brazil`, `israel`, `automatic`, `indonesia`, `taiwan`, `malaysia`, `newZealand`, `austria`, `denmark`, `belgium`, `kenya`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `norway`, `switzerland`, `southKorea`, `middleEast`, `mexico`, `australasia`, `europe`, `singapore`, `hongKong`, `ireland`, `sweden`, `poland`, `italy`, `spain`, `netherlands`, `brazil`, `israel`, `automatic`, `indonesia`, `taiwan`, `malaysia`, `newZealand`, `austria`, `denmark`, `belgium`, `kenya`. The default value is `automatic`. |
| regions | String collection | The list of region names within the region group. The default value is `automatic`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcRegionGroupConfiguration",
  "regionGroup": "String",
  "regions": ["String"]
}
```
