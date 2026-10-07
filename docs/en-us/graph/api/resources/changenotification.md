<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/changenotification?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-01 -->

# changeNotification resource type

Namespace: microsoft.graph

Represents the notification sent to the subscriber \(app\) of a [Microsoft Graph subscription](https://learn.microsoft.com/en-us/graph/api/resources/subscription?view=graph-rest-1.0). All the properties of this resource are read-only.

For details, see [Use Microsoft Graph to get change notifications](https://learn.microsoft.com/en-us/graph/api/resources/change-notifications-api-overview?view=graph-rest-1.0).

## Methods

None.

## Properties

> **Note:**  
> The **changeType** property is required and only present in change notifications. The **lifecycleEvent** property is required and only present in lifecycle notifications. These two properties are mutually exclusive; a notification will include only one of them.

| Property | Type | Description |
| :--- | :--- | :--- |
| changeType | [changeType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-1.0#changetype-values) | Indicates the type of change that will raise the change notification. Required and only present for change notifications. Mutually exclusive with **lifecycleEvent**. The possible values are: `created`, `updated`, `deleted`, `unknownFutureValue`. `unknownFutureValue` is an evolvable enumeration sentinel reserved for future extensibility. Its addition does not introduce a new notification change type or change existing notification delivery. |
| clientState | string | Value of the **clientState** property sent in the subscription request \(if any\). The maximum length is 255 characters. The client can check whether the change notification came from the service by comparing the values of the **clientState** property. The value of the **clientState** property sent with the subscription is compared with the value of the **clientState** property received with each change notification. Optional. |
| encryptedContent | [changeNotificationEncryptedContent](https://learn.microsoft.com/en-us/graph/api/resources/changenotificationencryptedcontent?view=graph-rest-1.0) | \(Preview\) Encrypted content attached with the change notification. Only provided if **encryptionCertificate** and **includeResourceData** were defined during the subscription request and if the resource supports it. Optional. |
| id | string | Unique ID for the notification. Optional. |
| lifecycleEvent | lifecycleEventType | The type of lifecycle notification. Required and only present for lifecycle notifications. Mutually exclusive with **changeType**. Supported values: `missed`, `subscriptionRemoved`, `reauthorizationRequired`. |
| resource | String | The URI of the resource that emitted the change notification relative to `https://graph.microsoft.com`. Required. |
| resourceData | [resourceData](https://learn.microsoft.com/en-us/graph/api/resources/resourcedata?view=graph-rest-1.0) | The content of this property depends on the type of resource being subscribed to. Optional. |
| subscriptionExpirationDateTime | DateTimeOffset | The expiration time for the subscription. Required. |
| subscriptionId | Guid | The unique identifier of the subscription that generated the notification.Required. |
| tenantId | Guid | The unique identifier of the tenant from which the change notification originated. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.changeNotification",
  "changeType": "String",
  "clientState": "String",
  "encryptedContent": {
    "@odata.type": "microsoft.graph.changeNotificationEncryptedContent"
  },
  "id": "String (identifier)",
  "lifecycleEvent": "String",
  "resource": "String",
  "resourceData": {
    "@odata.type": "microsoft.graph.resourceData"
  },
  "subscriptionExpirationDateTime": "String (timestamp)",
  "subscriptionId": "Guid",
  "tenantId": "Guid"
}
```
