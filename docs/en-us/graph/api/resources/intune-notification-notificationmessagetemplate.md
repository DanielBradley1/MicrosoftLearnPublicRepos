<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationmessagetemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# notificationMessageTemplate resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Notification messages are messages that are sent to end users who are determined to be not-compliant with the compliance policies defined by the administrator. Administrators choose notifications and configure them in the Intune Admin Console using the compliance policy creation page under the “Actions for non-compliance” section. Use the notificationMessageTemplate object to create your own custom notifications for administrators to choose while configuring actions for non-compliance.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List notificationMessageTemplates](https://learn.microsoft.com/en-us/graph/api/intune-notification-notificationmessagetemplate-list?view=graph-rest-1.0) | [notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationmessagetemplate?view=graph-rest-1.0) collection | List properties and relationships of the [notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationmessagetemplate?view=graph-rest-1.0) objects. |
| [Get notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/intune-notification-notificationmessagetemplate-get?view=graph-rest-1.0) | [notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationmessagetemplate?view=graph-rest-1.0) | Read properties and relationships of the [notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationmessagetemplate?view=graph-rest-1.0) object. |
| [Create notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/intune-notification-notificationmessagetemplate-create?view=graph-rest-1.0) | [notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationmessagetemplate?view=graph-rest-1.0) | Create a new [notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationmessagetemplate?view=graph-rest-1.0) object. |
| [Delete notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/intune-notification-notificationmessagetemplate-delete?view=graph-rest-1.0) | None | Deletes a [notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationmessagetemplate?view=graph-rest-1.0). |
| [Update notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/intune-notification-notificationmessagetemplate-update?view=graph-rest-1.0) | [notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationmessagetemplate?view=graph-rest-1.0) | Update the properties of a [notificationMessageTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationmessagetemplate?view=graph-rest-1.0) object. |
| [sendTestMessage action](https://learn.microsoft.com/en-us/graph/api/intune-notification-notificationmessagetemplate-sendtestmessage?view=graph-rest-1.0) | None | Sends test message using the specified notificationMessageTemplate in the default locale |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. |
| displayName | String | Display name for the Notification Message Template. |
| description | String | Display name for the Notification Message Template. |
| defaultLocale | String | The default locale to fallback onto when the requested locale is not available. |
| brandingOptions | [notificationTemplateBrandingOptions](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-notificationtemplatebrandingoptions?view=graph-rest-1.0) | The Message Template Branding Options. Branding is defined in the Intune Admin Console. The possible values are: `none`, `includeCompanyLogo`, `includeCompanyName`, `includeContactInformation`, `includeCompanyPortalLink`, `includeDeviceDetails`, `unknownFutureValue`. |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| localizedNotificationMessages | [localizedNotificationMessage](https://learn.microsoft.com/en-us/graph/api/resources/intune-notification-localizednotificationmessage?view=graph-rest-1.0) collection | The list of localized messages for this Notification Message Template. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.notificationMessageTemplate",
  "id": "String (identifier)",
  "lastModifiedDateTime": "String (timestamp)",
  "displayName": "String",
  "description": "String",
  "defaultLocale": "String",
  "brandingOptions": "String",
  "roleScopeTagIds": [
    "String"
  ]
}
```
