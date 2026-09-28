<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-notificationchannel?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# notificationChannel resource type

Namespace: microsoft.graph.deviceManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information about the notification channels of an [alert rule](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-alertrule?view=graph-rest-beta) selected by a user.

Note

This API is part of the [alert monitoring API set](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-monitoring?view=graph-rest-beta&preserve-view=true) which currently supports only [Windows 365](https://learn.microsoft.com/en-us/windows-365/overview) and Cloud PC scenarios. The API set allows admins to set up rules to alert issues with provisioning Cloud PCs, uploading Cloud PC images, and checking Azure network connections.

Have a different scenario that can use additional programmatic alert support on the Microsoft Endpoint Manager admin center? [Suggest the feature or vote for existing feature requests](https://developer.microsoft.com/en-us/graph/support).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| notificationChannelType | [microsoft.graph.deviceManagement.notificationChannelType](#notificationchanneltype-values) | The type of the notification channel. The possible values are: `portal`, `email`, `phoneCall`, `sms`, `unknownFutureValue`. |
| notificationReceivers | [microsoft.graph.deviceManagement.notificationReceiver](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-notificationreceiver?view=graph-rest-beta) collection | Information about the notification receivers, such as locale and contact information. For example, `en-us` for locale and `serena.davis@contoso.com` for contact information. |

### notificationChannelType values

| Member | Description |
| :--- | :--- |
| portal | Indicates that the notification message was published via the Microsoft Endpoint Manager admin center. |
| email | Indicates that the notification message was published via email. |
| phoneCall | Indicates that the notification message was published via phone call. |
| sms | Indicates that the notification message was published via SMS. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagement.notificationChannel",
  "notificationChannelType": "String",
  "notificationReceivers": [
    {
        "@odata.type": "#microsoft.graph.deviceManagement.notificationReceiver"
    }
  ]
}
```
