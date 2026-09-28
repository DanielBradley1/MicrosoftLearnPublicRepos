<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/mobiledriverslicenseconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# mobileDriversLicenseConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains settings for accepting mobile driver's licenses through the **mobileDriversLicenseConfiguration** property of a [verifiedIdProfile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| acceptedRegions | String collection | The ISO 3166-2 region codes accepted for mobile driver's licenses. An empty collection indicates all regions are accepted. |
| documentStandard | String | The document standard that accepted mobile driver's licenses must use, such as ISO18013-5. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.mobileDriversLicenseConfiguration",
  "acceptedRegions": [
    "String"
  ],
  "documentStandard": "String"
}
```
