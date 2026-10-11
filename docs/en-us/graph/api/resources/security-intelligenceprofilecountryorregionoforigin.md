<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofilecountryorregionoforigin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-06 -->

# intelligenceProfileCountryOrRegionOfOrigin resource type

Namespace: microsoft.graph.security

Note

The Microsoft Threat Intelligence APIs are available to all customers with a Microsoft Defender XDR or Microsoft Sentinel license. No separate license is required to access these APIs.

Represents a country/region of origin for an actor related to a threat or vulnerability outlined in an intelligence profile.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | A codified representation for this country/region of origin. |
| label | String | A display label for this ountry/region of origin. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.intelligenceProfileCountryOrRegionOfOrigin",
  "code": "String",
  "label": "String"
}
```
