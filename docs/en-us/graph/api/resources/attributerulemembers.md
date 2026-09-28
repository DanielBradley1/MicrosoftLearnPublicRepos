<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/attributerulemembers?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# attributeRuleMembers resource type

Namespace: microsoft.graph

Identifies a collection of users in the tenant who will be assigned the access package automatically based on the specified membership rule.

Used in the **specificAllowedTargets** setting of an [access package assignment policy](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentpolicy?view=graph-rest-1.0). Inherits from [subjectSet](https://learn.microsoft.com/en-us/graph/api/resources/subjectset?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | A description of the membership rule. |
| membershipRule | String | Determines the allowed target users for this policy. For more information about the syntax of the membership rule, see [Membership Rules syntax](https://learn.microsoft.com/en-us/azure/active-directory/enterprise-users/groups-dynamic-membership). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.attributeRuleMembers",
  "description": "String",
  "membershipRule": "String"
}
```
