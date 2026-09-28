<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-macosappscript?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# macOSAppScript resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Shell script used to assist installation of a macOS app. These scripts are used to perform additional tasks to help the app successfully be configured.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| scriptContent | String | The base64 encoded shell script \(.sh\) that assists managing macOS apps. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.macOSAppScript",
  "scriptContent": "String"
}
```
