<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaignreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# trainingCampaignReport resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a report of a training campaign, including an overview and a list of the users who participated in the campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| campaignUsers | [userSimulationDetails](https://learn.microsoft.com/en-us/graph/api/resources/usersimulationdetails?view=graph-rest-beta) collection | The overview of the attack simulation and training campaign. |
| overview | [trainingCampaignReportOverview](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaignreportoverview?view=graph-rest-beta) | The tenant users and their online actions in a training campaign. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trainingCampaignReport",
  "overview": {
    "@odata.type": "microsoft.graph.trainingCampaignReportOverview"
  },
  "campaignUsers": [
    {
      "@odata.type": "microsoft.graph.userSimulationDetails"
    }
  ]
}
```
