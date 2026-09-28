<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaignreportoverview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# trainingCampaignReportOverview resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an overview report of a training campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| trainingModuleCompletion | [trainingEventsContent](https://learn.microsoft.com/en-us/graph/api/resources/trainingeventscontent?view=graph-rest-beta) | Aggregate data of training completion. |
| trainingNotificationDeliveryStatus | [trainingNotificationDelivery](https://learn.microsoft.com/en-us/graph/api/resources/trainingnotificationdelivery?view=graph-rest-beta) | Aggregate data of training mail delivery over the course of the training campaign. |
| userCompletionStatus | [userTrainingCompletionSummary](https://learn.microsoft.com/en-us/graph/api/resources/usertrainingcompletionsummary?view=graph-rest-beta) | Aggregate data of users training progress. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trainingCampaignReportOverview",
  "trainingModuleCompletion": {
    "@odata.type": "microsoft.graph.trainingEventsContent"
  },
  "userCompletionStatus": {
    "@odata.type": "microsoft.graph.userTrainingCompletionSummary"
  },
  "trainingNotificationDeliveryStatus": {
    "@odata.type": "microsoft.graph.trainingNotificationDelivery"
  }
}
```
