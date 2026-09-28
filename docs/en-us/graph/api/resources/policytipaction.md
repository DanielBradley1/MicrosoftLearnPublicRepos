<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/policytipaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# policyTipAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

When a Data Loss Prevention \(DLP\) policy is triggered, guidance to display to the user is included as a policy tip. The **policyTipAction** is returned in the processContent and protectionScopes responses when a DLP policy with a notify-user action matches.

Inherits from [dlpActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.security.dlpAction | The type of DLP action. Inherited from [dlpActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-beta). |
| complianceUrl | String | A URL that points users to additional compliance guidance or remediation details for the policy tip. |
| matchedConditionsDescription | String | A user-friendly summary of the matched DLP conditions that triggered the policy tip. |
| policyTip | String | The text of the policy tip that explains what triggered the DLP policy. Developers can display this information to users in the app. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.policyTipAction",
  "action": "policyTip",
  "complianceUrl": "String",
  "matchedConditionsDescription": "String",
  "policyTip": "String"
}
```
