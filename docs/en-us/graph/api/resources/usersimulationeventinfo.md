<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usersimulationeventinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# userSimulationEventInfo resource type

Namespace: microsoft.graph

Represents a simulation event of a user in a tenant in an attack simulation and training campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| browser | String | Browser information from where the simulation event was initiated by a user in an attack simulation and training campaign. |
| eventDateTime | DateTimeOffset | Date and time of the simulation event by a user in an attack simulation and training campaign. |
| eventName | String | Name of the simulation event by a user in an attack simulation and training campaign. |
| ipAddress | String | IP address from where the simulation event was initiated by a user in an attack simulation and training campaign. |
| osPlatformDeviceDetails | String | The operating system, platform, and device details from where the simulation event was initiated by a user in an attack simulation and training campaign. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userSimulationEventInfo",
  "browser": "String",
  "eventDateTime": "String (timestamp)",
  "eventName": "String",
  "ipAddress": "String",
  "osPlatformDeviceDetails": "String"
}
```
