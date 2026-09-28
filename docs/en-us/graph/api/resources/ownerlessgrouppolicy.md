<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# ownerlessGroupPolicy resource type

Namespace: microsoft.graph

Represents the configuration for managing [Microsoft 365 groups](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-1.0) that have lost their sole owner. Use this policy to send actionable notification emails to active members of ownerless groups to accept ownership. Administrators can configure notification duration, maximum members to notify, and control ownership eligibility by using security groups.

For more information, see [Manage ownerless Microsoft 365 groups and teams](https://learn.microsoft.com/en-us/microsoft-365/admin/create-groups/ownerless-groups-teams)

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/ownerlessgrouppolicy-get?view=graph-rest-1.0) | [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0) | Read the properties of an [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0) object. |
| [Upsert](https://learn.microsoft.com/en-us/graph/api/ownerlessgrouppolicy-upsert?view=graph-rest-1.0) | [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0) | Create or update an [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emailInfo | [emailDetails](https://learn.microsoft.com/en-us/graph/api/resources/emaildetails?view=graph-rest-1.0) | The email notification details for the ownerless group policy, including the sender, subject, and body. |
| enabledGroupIds | String collection | The collection of IDs for groups to which the policy is enabled. If empty, the policy is enabled for all groups in the tenant. |
| isEnabled | Boolean | Indicates whether the ownerless group policy is enabled in the tenant. Setting this property to `false` clears the values of all other policy parameters. |
| maxMembersToNotify | Int64 | The maximum number of members to notify. Value range is 0-90. Members are prioritized by recent group activity \(most active first\). If there aren't enough active members to fill the limit, remaining slots are filled with other eligible group members from the directory. |
| notificationDurationInWeeks | Int64 | The number of weeks for the notification duration. Value range is 1-7. |
| policyWebUrl | String | The URL to the policy documentation. |
| targetOwners | [targetOwners](https://learn.microsoft.com/en-us/graph/api/resources/targetowners?view=graph-rest-1.0) | The criteria for selecting target owners for the ownerless group. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.ownerlessGroupPolicy",
  "isEnabled": "Boolean",
  "notificationDurationInWeeks": "Int64",
  "maxMembersToNotify": "Int64",
  "enabledGroupIds": [
    "String"
  ],
  "emailInfo": {
    "@odata.type": "microsoft.graph.emailDetails"
  },
  "policyWebUrl": "String",
  "targetOwners": {
    "@odata.type": "microsoft.graph.targetOwners"
  }
}
```
