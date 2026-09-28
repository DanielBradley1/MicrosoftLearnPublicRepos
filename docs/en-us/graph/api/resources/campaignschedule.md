<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/campaignschedule?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-10 -->

# campaignSchedule resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a schedule for launching a campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| completionDateTime | DateTimeOffset | The date and time at which the campaign completed. |
| launchDateTime | DateTimeOffset | The date and time at which the campaign was launched. |
| status | campaignStatus | The current state of the campaign. The possible values are: `unknown`, `draft`, `inProgress`, `scheduled`, `completed`, `failed`, `cancelled`, `excluded`, `deleted`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.campaignSchedule",
  "completionDateTime": "String (timestamp)",
  "launchDateTime": "String (timestamp)",
  "status": "String"
}
```
