<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrulecontrols?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# conditionalAccessPolicyRuleControls resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the grant and session controls configured in the **controls** property of a [conditionalAccessPolicyRule](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesspolicyrule?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| grantControls | [conditionalAccessGrantControls](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessgrantcontrols?view=graph-rest-beta) | The grant controls to enforce, such as multifactor authentication, a compliant device, or blocking access. |
| sessionControls | [conditionalAccessSessionControls](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrols?view=graph-rest-beta) | The session controls to enforce, such as sign-in frequency or persistent browser settings. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.conditionalAccessPolicyRuleControls",
  "grantControls": {
    "@odata.type": "microsoft.graph.conditionalAccessGrantControls"
  },
  "sessionControls": {
    "@odata.type": "microsoft.graph.conditionalAccessSessionControls"
  }
}
```
