<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-attacksimulationinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# attackSimulationInfo resource type

Namespace: microsoft.graph.security

Represents attack simulation information for threat submission. If an email was an attack simulation email, the email threat submission would contain corresponding attack simulation information.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| attackSimDateTime | DateTimeOffset | The date and time of the attack simulation. |
| attackSimDurationTime | Duration | The duration \(in time\) for the attack simulation. |
| attackSimId | Guid | The activity ID for the attack simulation. |
| attackSimUserId | String | The unique identifier for the user who got the attack simulation email. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.attackSimulationInfo",
  "attackSimDateTime": "String (timestamp)",  
  "attackSimDurationTime": "String (duration)",
  "attackSimId": "Guid",
  "attackSimUserId": "String"
}
```
