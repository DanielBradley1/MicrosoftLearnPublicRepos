<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcmicrosofthostednetworkconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-05-19 -->

# cloudPcMicrosoftHostedNetworkConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Microsoft-hosted network configuration settings for Cloud PC provisioning.

Inherits from [cloudPcNetworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcnetworkconfiguration?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| geographicLocationType | [cloudPcGeographicLocationType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcgeographiclocationtype?view=graph-rest-beta) | The geographic location type for the network. The possible values are: `default`, `asia`, `australasia`, `canada`, `europe`, `india`, `africa`, `usCentral`, `usEast`, `usWest`, `southAmerica`, `middleEast`, `centralAmerica`, `usGovernment`, `unknownFutureValue`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `mexico`. |
| regionGroups | [cloudPcRegionGroupConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcregiongroupconfiguration?view=graph-rest-beta) collection | The region group configurations for the network. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcMicrosoftHostedNetworkConfiguration",
  "geographicLocationType": "String",
  "regionGroups": [
    {
      "@odata.type": "microsoft.graph.cloudPcRegionGroupConfiguration"
    }
  ]
}
```
