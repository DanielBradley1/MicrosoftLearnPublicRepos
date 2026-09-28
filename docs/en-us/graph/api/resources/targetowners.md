<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/targetowners?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# targetOwners resource type

Namespace: microsoft.graph

Represents the criteria for selecting target owners in an [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0). Controls which group members are eligible to receive ownership notification emails based on security group membership.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| notifyMembers | notifyMembers | The strategy for selecting members to notify about taking ownership. The possible values are: `all`, `allowSelected`, `blockSelected`. |
| securityGroups | String collection | The collection of IDs for security groups used for allowing or blocking filtering. When **notifyMembers** is `all`, all members are eligible for ownership and this collection can be empty. When **notifyMembers** is `allowSelected`, only members in these security groups are eligible. When **notifyMembers** is `blockSelected`, members in these security groups are excluded. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.targetOwners",
  "notifyMembers": "String",
  "securityGroups": [
    "String"
  ]
}
```
