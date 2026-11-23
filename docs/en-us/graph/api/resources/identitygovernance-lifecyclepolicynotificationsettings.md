<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicynotificationsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicyNotificationSettings resource type

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the notification settings for a lifecycle policy, including when notifications are sent after an identity becomes non-compliant. This type is configured in the **notificationSchedule** property of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalFallbackRecipients | String collection | The email addresses used when no targeted notification recipient has a valid email address. These addresses aren't copied on every notification or used alongside a valid targeted recipient. |
| offsetsAfterNonComplianceInDays | Int32 collection | The offsets, in days after an identity becomes non-compliant, at which notifications are sent. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecyclePolicyNotificationSettings",
  "additionalFallbackRecipients": [
    "String"
  ],
  "offsetsAfterNonComplianceInDays": [
    "Integer"
  ]
}
```
