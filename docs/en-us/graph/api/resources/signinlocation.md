<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/signinlocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# signInLocation resource type

Namespace: microsoft.graph

Provides the city, state and country/region from where the sign-in happened. This object is configured in the **location** property of [signIn](https://learn.microsoft.com/en-us/graph/api/resources/signin?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| city | String | Provides the city where the sign-in originated and is determined using latitude/longitude information from the sign-in activity. |
| countryOrRegion | String | Provides the country code info \(two letter code\) where the sign-in originated. This is calculated using latitude/longitude information from the sign-in activity. |
| geoCoordinates | [geoCoordinates](https://learn.microsoft.com/en-us/graph/api/resources/geocoordinates?view=graph-rest-1.0) | Provides the latitude, longitude and altitude where the sign-in originated. |
| state | String | Provides the State where the sign-in originated. This is calculated using latitude/longitude information from the sign-in activity. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "city": "String",
  "countryOrRegion": "String",
  "geoCoordinates": {"@odata.type": "microsoft.graph.geoCoordinates"},
  "state": "String"
}
```
