<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-appleapplistitem?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# appleAppListItem resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents an app in the list of managed Apple applications

Inherits from [appListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applistitem?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| name | String | The application name Inherited from [appListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applistitem?view=graph-rest-beta) |
| publisher | String | The publisher of the application Inherited from [appListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applistitem?view=graph-rest-beta) |
| appStoreUrl | String | The Store URL of the application Inherited from [appListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applistitem?view=graph-rest-beta) |
| appId | String | The application or bundle identifier of the application Inherited from [appListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applistitem?view=graph-rest-beta) |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.appleAppListItem",
  "name": "String",
  "publisher": "String",
  "appStoreUrl": "String",
  "appId": "String"
}
```
