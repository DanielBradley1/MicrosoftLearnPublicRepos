<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/chatmessagepolicyviolationpolicytip?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# chatMessagePolicyTip resource type

Represents the properties of a policy tip on a [chatMessagePolicyViolation](https://learn.microsoft.com/en-us/graph/api/resources/chatmessagepolicyviolation?view=graph-rest-1.0) object. Policy tips provide the sender with information about the policy violation. Policy tips are typically set by a data loss prevention \(DLP\) app which watches for messages that contain data that users aren't supposed to send.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| complianceUrl | string | The URL a user can visit to read about the data loss prevention policies for the organization. \(ie, policies about what users shouldn't say in chats\) |
| generalText | string | Explanatory text shown to the sender of the message. |
| matchedConditionDescriptions | string collection | The list of improper data in the message that was detected by the data loss prevention app. Each DLP app defines its own conditions, examples include "Credit Card Number" and "Social Security Number". |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "complianceUrl": "string",
  "generalText": "string",
  "matchedConditionDescriptions": ["string 1", "string 2"]
}
```
