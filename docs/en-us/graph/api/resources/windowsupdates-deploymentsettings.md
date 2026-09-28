<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# deploymentSettings resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings that determine when and how Windows Autopatch deploys an update.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contentApplicability | [microsoft.graph.windowsUpdates.contentApplicabilitySettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapplicabilitysettings?view=graph-rest-beta) | Settings for governing whether content is applicable to a device. |
| expedite | [microsoft.graph.windowsUpdates.expediteSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-expeditesettings?view=graph-rest-beta) | Settings for governing whether updates should be expedited. |
| monitoring | [microsoft.graph.windowsUpdates.monitoringSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-monitoringsettings?view=graph-rest-beta) | Settings for governing conditions to monitor and automated actions to take. |
| schedule | [microsoft.graph.windowsUpdates.scheduleSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-schedulesettings?view=graph-rest-beta) | Settings for governing how and when the content is rolled out. |
| userExperience | [microsoft.graph.windowsUpdates.userExperienceSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-userexperiencesettings?view=graph-rest-beta) | Settings for governing end user update experience. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.deploymentSettings",
  "contentApplicability": {"@odata.type": "microsoft.graph.windowsUpdates.contentApplicabilitySettings"},
  "expedite": {"@odata.type": "microsoft.graph.windowsUpdates.expediteSettings"},
  "monitoring": {"@odata.type": "microsoft.graph.windowsUpdates.monitoringSettings"},
  "schedule": {"@odata.type": "microsoft.graph.windowsUpdates.scheduleSettings"},
  "userExperience": {"@odata.type": "microsoft.graph.windowsUpdates.userExperienceSettings"}
}
```
