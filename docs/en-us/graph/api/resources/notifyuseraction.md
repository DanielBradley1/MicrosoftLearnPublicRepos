<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/notifyuseraction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# notifyUserAction resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a Data Loss Prevention \(DLP\) action that involves notifying users about a policy match.

Inherits from [policyTipAction](https://learn.microsoft.com/en-us/graph/api/resources/policytipaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | microsoft.graph.security.dlpAction | The type of DLP action. Possible values are `notifyUser`, `blockAccess`, `restrictAccess`, `generateAlert`, `generateIncidentReportAction`, `sPBlockAnonymousAccess`, `sPRuntimeAccessControl`, `sPSharingNotifyUser`, and `sPSharingGenerateIncidentReport`. Inherited from [dlpActionInfo](https://learn.microsoft.com/en-us/graph/api/resources/dlpactioninfo?view=graph-rest-beta). |
| actionLastModifiedDateTime | DateTimeOffset | Timestamp when the notification action configuration was last modified. |
| emailText | String | The body text of the email notification sent to users. |
| overrideOption | microsoft.graph.security.overrideOption | Specifies the override options available to the user. Possible values are `notAllowed`, `allowFalsePositiveOverride`, `allowWithJustification`, `allowWithoutJustification`, and `allowWithAcknowledgement`. |
| policyTip | String | The text of the policy tip displayed to the user within the application \(For example, Outlook, Word\). Inherited from [policyTipAction](https://learn.microsoft.com/en-us/graph/api/resources/policytipaction?view=graph-rest-beta). |
| recipients | String collection | List of email addresses or user identifiers designated to receive the notification email. Can include sender, owner, manager, etc. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.notifyUserAction",
  "action": "notifyUser",

  "recipients": [
    "String"
  ],
  "actionLastModifiedDateTime": "String (timestamp)",
  "overrideOption": "String",
  "emailText": "String",
  "policyTip": "String"
}
```
