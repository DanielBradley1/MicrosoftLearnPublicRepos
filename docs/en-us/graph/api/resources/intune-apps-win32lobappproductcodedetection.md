<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappproductcodedetection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# win32LobAppProductCodeDetection resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains product code and version properties to detect a Win32 App

Inherits from [win32LobAppDetection](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappdetection?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| productCode | String | The product code of Win32 Line of Business \(LoB\) app. |
| productVersionOperator | [win32LobAppDetectionOperator](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-win32lobappdetectionoperator?view=graph-rest-beta) | The operator to detect product version. Possible values are: `notConfigured`, `equal`, `notEqual`, `greaterThan`, `greaterThanOrEqual`, `lessThan`, `lessThanOrEqual`. |
| productVersion | String | The product version of Win32 Line of Business \(LoB\) app. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.win32LobAppProductCodeDetection",
  "productCode": "String",
  "productVersionOperator": "String",
  "productVersion": "String"
}
```
