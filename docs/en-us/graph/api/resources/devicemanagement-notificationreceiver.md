<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-notificationreceiver?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# notificationReceiver resource type

Namespace: microsoft.graph.deviceManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the locale and contact information provided by a user in a [notification channel](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-notificationchannel?view=graph-rest-beta).

Note

This API is part of the [alert monitoring API set](https://learn.microsoft.com/en-us/graph/api/resources/devicemanagement-monitoring?view=graph-rest-beta&preserve-view=true) which currently supports only [Windows 365](https://learn.microsoft.com/en-us/windows-365/overview) and Cloud PC scenarios. The API set allows admins to set up rules to alert issues with provisioning Cloud PCs, uploading Cloud PC images, and checking Azure network connections.

Have a different scenario that can use additional programmatic alert support on the Microsoft Endpoint Manager admin center? [Suggest the feature or vote for existing feature requests](https://developer.microsoft.com/en-us/graph/support).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contactInformation | String | The contact information about the notification receivers, such as an email address. Currently, only email and portal notifications are supported. For portal notifications, **contactInformation** can be left blank. For email notifications, **contactInformation** consists of an email address such as `serena.davis@contoso.com`. |
| locale | String | Defines the language and format in which the notification will be sent. Supported locale values are: `en-us`, `cs-cz`, `de-de`, `es-es`, `fr-fr`, `hu-hu`, `it-it`, `ja-jp`, `ko-kr`, `nl-nl`, `pl-pl`, `pt-br`, `pt-pt`, `ru-ru`, `sv-se`, `tr-tr`, `zh-cn`, `zh-tw`. |

## Relationships

None.

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagement.notificationReceiver",
  "contactInformation": "String",
  "locale": "String"
}
```
