<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/emaildetails?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# emailDetails resource type

Namespace: microsoft.graph

Represents the email notification configuration for an [ownerlessGroupPolicy](https://learn.microsoft.com/en-us/graph/api/resources/ownerlessgrouppolicy?view=graph-rest-1.0). Contains the sender, subject, and body of the notification email sent to group members.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| body | String | The body content of the notification email in plain text format. |
| senderEmailAddress | String | The email address of the sender for notification emails. Shared mailboxes aren't supported. |
| subject | String | The subject line of the notification email. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.emailDetails",
  "senderEmailAddress": "String",
  "subject": "String",
  "body": "String"
}
```
