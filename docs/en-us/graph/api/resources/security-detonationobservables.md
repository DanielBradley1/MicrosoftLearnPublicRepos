<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-detonationobservables?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# detonationObservables resource type

Namespace: microsoft.graph.security

Represents the resources that a detonation includes, such as URLs, IPs, domains, and files. These resources can be either problematic or benign. It is returned in the **detonationObservables** property of [detonationDetails](https://learn.microsoft.com/en-us/graph/api/resources/security-detonationdetails?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contactedIps | String collection | The list of all contacted IPs in the detonation. |
| contactedUrls | String collection | The list of all URLs found in the detonation. |
| droppedfiles | String collection | The list of all dropped files in the detonation. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.detonationObservables",
  "droppedfiles": [
    "String"
  ],
  "contactedIps": [
    "String"
  ],
  "contactedUrls": [
    "String"
  ]
}
```
