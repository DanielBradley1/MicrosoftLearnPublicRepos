<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/trainingnotificationdelivery?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# trainingNotificationDelivery resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains aggregate data about training mail delivery over the course of the training campaign.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| failedMessageDeliveryCount | Int32 | The number of users to whom mails couldn't be delivered. |
| resolvedTargetsCount | Int32 | The number of users whose email address was successfully resolved from target users. |
| successfulMessageDeliveryCount | Int32 | The number of users who received a mail while the training campaign was in the "in progress" state. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.trainingNotificationDelivery",
  "resolvedTargetsCount": "Integer",
  "successfulMessageDeliveryCount": "Integer",
  "failedMessageDeliveryCount": "Integer"
}
```
