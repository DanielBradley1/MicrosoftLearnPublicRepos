<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-27 -->

# countryNamedLocation resource type

Namespace: microsoft.graph

Represents a Microsoft Entra ID named location defined by countries and regions. Named locations are custom rules that define network locations which can then be used in a Conditional Access policy.

Inherits from [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-list-namedlocations?view=graph-rest-1.0) | [countryNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-1.0) collection | Get all the **countryNamedLocation** objects in the organization. |
| [Create](https://learn.microsoft.com/en-us/graph/api/conditionalaccessroot-post-namedlocations?view=graph-rest-1.0) | [countryNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-1.0) | Create a new **countryNamedLocation** object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/countrynamedlocation-get?view=graph-rest-1.0) | [countryNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-1.0) | Read the properties and relationships of a **countryNamedLocation** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/countrynamedlocation-update?view=graph-rest-1.0) | [countryNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/countrynamedlocation?view=graph-rest-1.0) | Update a **countryNamedLocation** object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/countrynamedlocation-delete?view=graph-rest-1.0) | None | Delete a **countryNamedLocation** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| countriesAndRegions | String collection | List of countries and/or regions in two-letter format specified by ISO 3166-2. Required. |
| countryLookupMethod | countryLookupMethodType | Determines what method is used to decide which country the user is located in. Possible values are `clientIpAddress`\(default\) and `authenticatorAppGps`. Note: `authenticatorAppGps` is not yet supported in the Microsoft Cloud for US Government. |
| createdDateTime | DateTimeOffset | The Timestamp type represents creation date and time of the location using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-1.0). |
| displayName | String | Human-readable name of the location. Required. Inherited from [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-1.0). |
| id | String | Identifier of a namedLocation object. Read-only. Inherited from [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-1.0). |
| includeUnknownCountriesAndRegions | Boolean | `true` if IP addresses that don't map to a country or region should be included in the named location. Optional. Default value is `false`. |
| modifiedDateTime | DateTimeOffset | The Timestamp type represents last modified date and time of the location using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Read-only. Inherited from [namedLocation](https://learn.microsoft.com/en-us/graph/api/resources/namedlocation?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "countriesAndRegions": ["String"],
  "countryLookupMethod": "String",
  "createdDateTime": "String (timestamp)",
  "displayName": "String",
  "id": "String (identifier)",
  "includeUnknownCountriesAndRegions": true,
  "modifiedDateTime": "String (timestamp)"
}
```

## Related content

- [What is Conditional Access?](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/overview)
- [Using the location condition in a Conditional Access policy](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/location-condition)
