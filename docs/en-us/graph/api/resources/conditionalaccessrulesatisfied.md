<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessrulesatisfied?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# conditionalAccessRuleSatisfied resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Indicates the attributes related to applied conditional access policy or policies that are triggered by the corresponding sign-in activity. This object is configured in the **excludeRulesSatisfied** and **includeRulesSatisfied** properties of [appliedConditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/appliedconditionalaccesspolicy?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| conditionalAccessCondition | conditionalAccessConditions | Refers to the conditional access policy conditions that are satisfied. The possible values are: `none`, `application`, `users`, `devicePlatform`, `location`, `clientType`, `signInRisk`, `userRisk`, `time`, `deviceState`, `client`, `ipAddressSeenByAzureAD`, `ipAddressSeenByResourceProvider`, `unknownFutureValue`, `servicePrincipals`, `servicePrincipalRisk`, `authenticationFlows`, `insiderRisk`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `servicePrincipals`, `servicePrincipalRisk`, `authenticationFlows`, `insiderRisk`. **conditionalAccessConditions** is a multi-valued enumeration and the property can contain multiple values in a comma-separated list. |
| ruleSatisfied | conditionalAccessRule | Refers to the conditional access policy conditions that were satisfied. The possible values are: `allApps`, `firstPartyApps`, `office365`, `appId`, `acr`, `appFilter`, `allUsers`, `guest`, `groupId`, `roleId`, `userId`, `allDevicePlatforms`, `devicePlatform`, `allLocations`, `insideCorpnet`, `allTrustedLocations`, `locationId`, `allDevices`, `deviceFilter`, `deviceState`, `unknownFutureValue`, `deviceFilterIncludeRuleNotMatched`, `allDeviceStates`, `anonymizedIPAddress`, `unfamiliarFeatures`, `nationStateIPAddress`, `realTimeThreatIntelligence`, `internalGuest`, `b2bCollaborationGuest`, `b2bCollaborationMember`, `b2bDirectConnectUser`, `otherExternalUser`, `serviceProvider`, `microsoftAdminPortals`, `deviceCodeFlow`, `accountTransfer`, `insiderRisk`. Use the `Prefer: include-unknown-enum-members` request header to get the following values in this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `deviceFilterIncludeRuleNotMatched`, `allDeviceStates`, `anonymizedIPAddress`, `unfamiliarFeatures`, `nationStateIPAddress`, `realTimeThreatIntelligence`, `internalGuest`, `b2bCollaborationGuest`, `b2bCollaborationMember`, `b2bDirectConnectUser`, `otherExternalUser`, `serviceProvider`, `microsoftAdminPortals`, `deviceCodeFlow`, `accountTransfer`, `insiderRisk`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessRuleSatisfied",
  "conditionalAccessCondition": "String",
  "ruleSatisfied": "String"
}
```
