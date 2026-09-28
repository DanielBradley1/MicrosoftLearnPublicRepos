<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usertrainingcontenteventinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# userTrainingContentEventInfo resource type

Namespace: microsoft.graph

Represents training event details of assigned trainings to users in an attack simulation and training campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| browser | String | Browser of the user from where the training event was generated. |
| contentDateTime | DateTimeOffset | Date and time of the training content playback by the user. |
| ipAddress | String | IP address of the user for the training event. |
| osPlatformDeviceDetails | String | The operating system, platform, and device details of the user for the training event. |
| potentialScoreImpact | Double | Potential improvement in the tenant security posture after completion of the training by the user. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userTrainingContentEventInfo",
  "browser": "String",
  "contentDateTime": "String (timestamp)",
  "ipAddress": "String",
  "osPlatformDeviceDetails": "String",
  "potentialScoreImpact": "Double"
}
```
