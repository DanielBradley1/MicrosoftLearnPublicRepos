<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessagepolicyviolation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-03 -->

# chatMessagePolicyViolation resource type

Represents a policy violation on a chat message. Policy violations are typically set by a data loss prevention \(DLP\) application. DLP applications monitor chats for messages that contain data that users aren't supposed to send.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dlpAction | **chatMessagePolicyViolationDlpActionType** | The action taken by the DLP provider on the message with sensitive content. Supported values are:<br><br><li>None</li><br><br><li>NotifySender -- Inform the sender of the violation but allow readers to read the message.</li><br><br><li>BlockAccess -- Block readers from reading the message.</li><br><br><li>BlockAccessExternal -- Block users outside the organization from reading the message, while allowing users within the organization to read the message.</li> |
| justificationText | string | Justification text provided by the sender of the message when overriding a policy violation. |
| policyTip | [chatMessagePolicyViolationPolicyTip](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagepolicyviolationpolicytip?view=graph-rest-1.0) | Information to display to the message sender about why the message was flagged as a violation. |
| userAction | **chatMessagePolicyViolationUserActionType** | Indicates the action taken by the user on a message blocked by the DLP provider. Supported values are:<br><br><li>None</li><br><br><li>Override</li><br><br><li>ReportFalsePositive</li><br><br>When the DLP provider is updating the message for blocking sensitive content, userAction isn't required. |
| verdictDetails | **chatMessagePolicyViolationVerdictDetailsType** | Indicates what actions the sender may take in response to the policy violation. Supported values are:<br><br><li>None</li><br><br><li>AllowFalsePositiveOverride -- Allows the sender to declare the policyViolation to be an error in the DLP app and its rules, and allow readers to see the message again if the dlpAction hides it.</li><br><br><li>AllowOverrideWithoutJustification -- Allows the sender to override the DLP violation and allow readers to see the message again if the dlpAction hides it, without needing to provide an explanation for doing so. </li><br><br><li>AllowOverrideWithJustification -- Allows the sender to override the DLP violation and allow readers to see the message again if the dlpAction hides it, after providing an explanation for doing so.</li><br><br>AllowOverrideWithoutJustification and AllowOverrideWithJustification are mutually exclusive. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "dlpAction": "string",
  "justificationText": "string",
  "policyTip": {"@odata.type": "microsoft.graph.chatMessagePolicyViolationPolicyTip"},
  "userAction": "string",
  "verdictDetails": "string"
}
```
