<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatecveseverityinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# qualityUpdateCveSeverityInformation resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the summary of severity information regarding the Common Vulnerabilities and Exposures \(CVEs\) addressed by a quality update. The national vulnerability database uses the Common Vulnerability Scoring System \(CVSS\) to supply a qualitative measure of severity. Each CVE has a severity level that can be `moderate`, `important`, or `critical` and a CVSS base score that ranges from `0.0` to `10.0`.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| exploitedCves | [microsoft.graph.windowsUpdates.cveInformation](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-cveinformation?view=graph-rest-beta) collection | Collection of information about each publicly exploited vulnerability addressed in the quality update. |
| maxBaseScore | Double | Highest base score that occurs of any CVE addressed by the quality update. Read-only. |
| maxSeverityLevel | microsoft.graph.windowsUpdates.cveSeverityLevel | Highest severity level that occurs of any CVE addressed by the quality update. The possible values are: `critical`, `important`, `moderate`, `unknownFutureValue`. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.qualityUpdateCveSeverityInformation",
  "exploitedCves": [{"@odata.type": "microsoft.graph.windowsUpdates.cveInformation"}],
  "maxBaseScore": "Double",
  "maxSeverityLevel": "String"
}
```
