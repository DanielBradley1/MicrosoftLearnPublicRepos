<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-cveinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# cveInformation resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the number and URL for a Common Vulnerability and Exposure \(CVE\).

Information about CVEs is maintained by the [Microsoft Security Response Center](https://msrc.microsoft.com/update-guide/vulnerability). The Microsoft Security Response Center investigates all reports of security vulnerabilities that affect Microsoft products and services, and provides the information as part of the ongoing effort to help you manage security risks and help keep your systems protected. Each security quality update may address many CVEs.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| number | String | Identifies the number of the CVE. Read-only. |
| url | String | URL to the full CVE information. Read-only. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.cveInformation",
  "number": "String (identifier)",
  "url": "String"
}
```
