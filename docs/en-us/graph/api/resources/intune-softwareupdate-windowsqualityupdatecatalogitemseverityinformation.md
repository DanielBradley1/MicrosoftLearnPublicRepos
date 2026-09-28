<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitemseverityinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsQualityUpdateCatalogItemSeverityInformation resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

CVE information of QU catalog item

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| maxSeverity | [windowsQualityUpdateCatalogItemSeverityMaxSeverity](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitemseveritymaxseverity?view=graph-rest-beta) | Max severity of CVE. The possible values are: `critical`, `important`, `moderate`, `unknownFutureValue`. |
| maxBaseScore | Double | Max base score of CVE |
| exploitedCves | [windowsQualityUpdateCatalogItemExploitedCve](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitemexploitedcve?view=graph-rest-beta) collection | Exploit cve details |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsQualityUpdateCatalogItemSeverityInformation",
  "maxSeverity": "String",
  "maxBaseScore": "4.2",
  "exploitedCves": [
    {
      "@odata.type": "microsoft.graph.windowsQualityUpdateCatalogItemExploitedCve",
      "number": "String",
      "url": "String"
    }
  ]
}
```
