<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-iossinglesignonsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# iosSingleSignOnSettings resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

iOS Kerberos authentication settings for single sign-on

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowedAppsList | [appListItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-applistitem?view=graph-rest-beta) collection | List of app identifiers that are allowed to use this login. If this field is omitted, the login applies to all applications on the device. This collection can contain a maximum of 500 elements. |
| allowedUrls | String collection | List of HTTP URLs that must be matched in order to use this login. With iOS 9.0 or later, a wildcard characters may be used. |
| displayName | String | The display name of login settings shown on the receiving device. |
| kerberosPrincipalName | String | A Kerberos principal name. If not provided, the user is prompted for one during profile installation. |
| kerberosRealm | String | A Kerberos realm name. Case sensitive. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.iosSingleSignOnSettings",
  "allowedAppsList": [
    {
      "@odata.type": "microsoft.graph.appListItem",
      "name": "String",
      "publisher": "String",
      "appStoreUrl": "String",
      "appId": "String"
    }
  ],
  "allowedUrls": [
    "String"
  ],
  "displayName": "String",
  "kerberosPrincipalName": "String",
  "kerberosRealm": "String"
}
```
