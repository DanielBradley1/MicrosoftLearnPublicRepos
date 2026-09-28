<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowspackageinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsPackageInformation resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Contains properties for the package information for a Windows line of business app. Used as property within windowsPhone81AppXBundle object, which is also being deprecated. This complex type will be deprecated in February 2023.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicableArchitecture | [windowsArchitecture](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsarchitecture?view=graph-rest-beta) | The Windows architecture for which this app can run on. Possible values are: `none`, `x86`, `x64`, `arm`, `neutral`, `arm64`. |
| displayName | String | The Display Name. |
| identityName | String | The Identity Name. |
| identityPublisher | String | The Identity Publisher. |
| identityResourceIdentifier | String | The Identity Resource Identifier. |
| identityVersion | String | The Identity Version. |
| minimumSupportedOperatingSystem | [windowsMinimumOperatingSystem](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-windowsminimumoperatingsystem?view=graph-rest-beta) | The value for the minimum applicable operating system. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsPackageInformation",
  "applicableArchitecture": "String",
  "displayName": "String",
  "identityName": "String",
  "identityPublisher": "String",
  "identityResourceIdentifier": "String",
  "identityVersion": "String",
  "minimumSupportedOperatingSystem": {
    "@odata.type": "microsoft.graph.windowsMinimumOperatingSystem",
    "v8_0": true,
    "v8_1": true,
    "v10_0": true,
    "v10_1607": true,
    "v10_1703": true,
    "v10_1709": true,
    "v10_1803": true,
    "v10_1809": true,
    "v10_1903": true,
    "v10_1909": true,
    "v10_2004": true,
    "v10_2H20": true,
    "v10_21H1": true
  }
}
```
