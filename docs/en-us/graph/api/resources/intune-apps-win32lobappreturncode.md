<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappreturncode?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# win32LobAppReturnCode resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains return code properties for a Win32 App

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| returnCode | Int32 | Return code. |
| type | [win32LobAppReturnCodeType](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappreturncodetype?view=graph-rest-1.0) | The type of return code. The possible values are: `failed`, `success`, `softReboot`, `hardReboot`, `retry`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppReturnCode",
  "returnCode": 1024,
  "type": "String"
}
```
