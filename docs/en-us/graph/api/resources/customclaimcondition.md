<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customclaimcondition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# customClaimCondition resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a claim condition associated with a particular claim configuration. The claim configuration is only applied if the condition is met.

Inherits from [customClaimConditionBase](https://learn.microsoft.com/en-us/graph/api/resources/customclaimconditionbase?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| memberOf | String collection | A list of groups \(GUIDs\) to which the user/application must be a member for this condition to be applied. |
| userType | claimConditionUserType | The type of user this condition applies to. The possible values are: `any`, `members`, `allGuests`, `aadGuests`, `externalGuests`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customClaimCondition",
  "userType": "String",
  "memberOf": [
    "String"
  ]
}
```
