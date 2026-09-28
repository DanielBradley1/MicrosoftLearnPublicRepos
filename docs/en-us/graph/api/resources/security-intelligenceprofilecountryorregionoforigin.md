<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-intelligenceprofilecountryorregionoforigin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# intelligenceProfileCountryOrRegionOfOrigin resource type

Namespace: microsoft.graph.security

Note

The Microsoft Graph API for Microsoft Defender Threat Intelligence requires an [active Defender Threat Intelligence Portal license and API add-on license](https://go.microsoft.com/fwlink/?linkid=2235706) for the tenant.

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
