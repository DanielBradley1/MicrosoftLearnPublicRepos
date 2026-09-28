<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessconditionset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# conditionalAccessConditionSet resource type

Namespace: microsoft.graph

Represents the type of conditions that govern when the policy applies.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applications | [conditionalAccessApplications](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessapplications?view=graph-rest-1.0) | Applications and user actions included in and excluded from the policy. Required. |
| authenticationFlows | [conditionalAccessAuthenticationFlows](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessauthenticationflows?view=graph-rest-1.0) | Authentication flows included in the policy scope. |
| clientApplications | [conditionalAccessClientApplications](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessclientapplications?view=graph-rest-1.0) | Client applications \(service principals and workload identities\) included in and excluded from the policy. Either **users** or **clientApplications** is required. |
| clientAppTypes | conditionalAccessClientApp collection | Client application types included in the policy. The possible values are: `all`, `browser`, `mobileAppsAndDesktopClients`, `exchangeActiveSync`, `easSupported`, `other`. Required.  <br>  <br>The `easUnsupported` enumeration member will be deprecated in favor of `exchangeActiveSync`, which includes EAS supported and unsupported platforms. |
| devices | [conditionalAccessDevices](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessdevices?view=graph-rest-1.0) | Devices in the policy. |
| locations | [conditionalAccessLocations](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesslocations?view=graph-rest-1.0) | Locations included in and excluded from the policy. |
| platforms | [conditionalAccessPlatforms](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessplatforms?view=graph-rest-1.0) | Platforms included in and excluded from the policy. |
| servicePrincipalRiskLevels | riskLevel collection | Service principal risk levels included in the policy. The possible values are: `low`, `medium`, `high`, `none`, `unknownFutureValue`. |
| signInRiskLevels | riskLevel collection | Sign-in risk levels included in the policy. The possible values are: `low`, `medium`, `high`, `hidden`, `none`, `unknownFutureValue`. Required. |
| userRiskLevels | riskLevel collection | User risk levels included in the policy. The possible values are: `low`, `medium`, `high`, `hidden`, `none`, `unknownFutureValue`. Required. |
| users | [conditionalAccessUsers](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessusers?view=graph-rest-1.0) | Users, groups, and roles included in and excluded from the policy. Either **users** or **clientApplications** is required. |
| insiderRiskLevels | conditionalAccessInsiderRiskLevels | Insider risk levels included in the policy. The possible values are: `minor`, `moderate`, `elevated`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessConditionSet",
  "applications": {"@odata.type": "microsoft.graph.conditionalAccessApplications"},
  "clientApplications": {"@odata.type": "microsoft.graph.conditionalAccessClientApplications"},
  "clientAppTypes": ["String"],
  "devices": {"@odata.type": "microsoft.graph.conditionalAccessDevices"},
  "locations": {"@odata.type": "microsoft.graph.conditionalAccessLocations"},
  "platforms": {"@odata.type": "microsoft.graph.conditionalAccessPlatforms"},
  "servicePrincipalRiskLevels": ["String"],
  "signInRiskLevels": ["String"],
  "userRiskLevels": ["String"],
  "users": {"@odata.type": "microsoft.graph.conditionalAccessUsers"},
  "insiderRiskLevels": "String",
  "authenticationFlows": {"@odata.type": "microsoft.graph.conditionalAccessAuthenticationFlows"}
}
```
