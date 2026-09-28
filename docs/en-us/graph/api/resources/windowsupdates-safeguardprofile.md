<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-safeguardprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# safeguardProfile resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes one or more issues against which Windows Autopatch safeguards devices.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| category | microsoft.graph.windowsUpdates.safeguardCategory | Specifies the category of safeguards. The possible values are: `likelyIssues`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.safeguardProfile",
  "category": "String"
}
```
