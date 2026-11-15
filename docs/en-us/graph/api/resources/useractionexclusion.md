<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/useractionexclusion?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# userActionExclusion resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a user-action exclusion in the **userActionExclusions** collection of [allResourcesExclusions](https://learn.microsoft.com/en-us/graph/api/resources/allresourcesexclusions?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| state | [conditionalAccessPolicyState](#conditionalaccesspolicystate-values) | The exclusion state. |
| userAction | String | The user action identifier, for example, `accountrecovery`. |

### conditionalAccessPolicyState values

The **state** property supports the following values.

| Member | Description |
| :--- | :--- |
| enabled | The exclusion is enabled. |
| disabled | The exclusion is disabled. |
| enabledForReportingButNotEnforced | The exclusion is evaluated in report-only mode. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.userActionExclusion",
  "state": "String",
  "userAction": "String"
}
```
