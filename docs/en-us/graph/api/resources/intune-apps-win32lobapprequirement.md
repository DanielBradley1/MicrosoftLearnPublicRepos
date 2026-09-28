<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobapprequirement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# win32LobAppRequirement resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Base class to detect a Win32 App

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| operator | [win32LobAppDetectionOperator](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappdetectionoperator?view=graph-rest-beta) | The operator for detection. Possible values are: `notConfigured`, `equal`, `notEqual`, `greaterThan`, `greaterThanOrEqual`, `lessThan`, `lessThanOrEqual`. |
| detectionValue | String | The detection value |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppRequirement",
  "operator": "String",
  "detectionValue": "String"
}
```
