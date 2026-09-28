<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-04 -->

# trainingCampaign resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a training campaign. In Attack simulation training in Microsoft 365 E5 or Microsoft Defender for Office 365 Plan 2, training campaigns are a fast, direct way to provide security training to users. Instead of creating and launching simulated phishing attacks that eventually lead to training, you can create and assign training campaigns directly to users.

A training campaign contains one or more built-in training modules that you select. Currently, there are over 70 training modules to select from. For more information about training modules, see training modules for Training campaigns in Attack simulation training.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-list-trainingcampaigns?view=graph-rest-beta) | [trainingCampaign](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta) collection | Get a list of the [trainingCampaign](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-post-trainingcampaigns?view=graph-rest-beta) | [trainingCampaign](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta) | Create a new [trainingCampaign](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/trainingcampaign-get?view=graph-rest-beta) | [trainingCampaign](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta) | Read the properties and relationships of a [trainingCampaign](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/trainingcampaign-update?view=graph-rest-beta) | [trainingCampaign](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta) | Update the properties of a [trainingCampaign](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/attacksimulationroot-delete-trainingcampaigns?view=graph-rest-beta) | None | Delete a [trainingCampaign](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaign?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| campaignSchedule | [campaignSchedule](https://learn.microsoft.com/en-us/graph/api/resources/campaignschedule?view=graph-rest-beta) | Details about the schedule and current status for a training campaign |
| createdBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-beta) | Identity of the user who created the training campaign |
| createdDateTime | DateTimeOffset | Date and time of creation of the training campaign. |
| description | String | Description of the training campaign. |
| displayName | String | Display name of the training campaign. Supports `$filter` and `$orderby`. |
| endUserNotificationSetting | [endUserNotificationSetting](https://learn.microsoft.com/en-us/graph/api/resources/endusernotificationsetting?view=graph-rest-beta) | Details about the end user notification setting. |
| excludedAccountTarget | [accountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-beta) | Users excluded from the training campaign. |
| id | String | Unique identifier for the training campaign. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| includedAccountTarget | [accountTargetContent](https://learn.microsoft.com/en-us/graph/api/resources/accounttargetcontent?view=graph-rest-beta) | Users targeted in the training campaign. |
| lastModifiedBy | [emailIdentity](https://learn.microsoft.com/en-us/graph/api/resources/emailidentity?view=graph-rest-beta) | Identity of the user who most recently modified the training campaign. |
| lastModifiedDateTime | DateTimeOffset | Date and time of the most recent modification of the training campaign. |
| report | [trainingCampaignReport](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaignreport?view=graph-rest-beta) | Report of the training campaign. |
| trainingSetting | [trainingSetting](https://learn.microsoft.com/en-us/graph/api/resources/trainingsetting?view=graph-rest-beta) | Details about the training settings for a training campaign. |

### campaignStatus values

| Member | Description |
| :--- | :--- |
| unknown | The campaign status isn't defined. |
| draft | The campaign is in draft mode. |
| inProgress | The campaign is in progress. |
| scheduled | The campaign is scheduled. |
| completed | The campaign is complete. |
| failed | The campaign failed. |
| cancelled | The campaign is cancelled. |
| excluded | The campaign is excluded. |
| deleted | The campaign is in draft mode. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trainingCampaign",
  "id": "String (identifier)",
  "createdBy": {
    "@odata.type": "microsoft.graph.emailIdentity"
  },
  "createdDateTime": "String (timestamp)",
  "description": "String",
  "displayName": "String",
  "endUserNotificationSetting": {
    "@odata.type": "microsoft.graph.endUserNotificationSetting"
  },
  "excludedAccountTarget": {
    "@odata.type": "microsoft.graph.accountTargetContent"
  },
  "includedAccountTarget": {
    "@odata.type": "microsoft.graph.accountTargetContent"
  },
  "lastModifiedBy": {
    "@odata.type": "microsoft.graph.emailIdentity"
  },
  "lastModifiedDateTime": "String (timestamp)",
  "report": {
    "@odata.type": "microsoft.graph.trainingCampaignReport"
  },
  "trainingSetting": {
    "@odata.type": "microsoft.graph.trainingSetting"
  },
  "campaignSchedule": {
    "@odata.type": "microsoft.graph.campaignSchedule"
  }
}
```

## Related content

- [Training campaigns in Attack simulation training](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/attack-simulation-training-training-campaigns?view=o365-worldwide&preserve-view=true)
