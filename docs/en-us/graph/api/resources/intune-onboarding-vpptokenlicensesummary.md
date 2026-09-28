<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptokenlicensesummary?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# vppTokenLicenseSummary resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

License summary of a given app in a token.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| vppTokenId | String | Identifier of the VPP token. |
| appleId | String | The Apple Id associated with the given Apple Volume Purchase Program Token. |
| organizationName | String | The organization associated with the Apple Volume Purchase Program Token. |
| availableLicenseCount | Int32 | The number of VPP licenses available. |
| usedLicenseCount | Int32 | The number of VPP licenses in use. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.vppTokenLicenseSummary",
  "vppTokenId": "String",
  "appleId": "String",
  "organizationName": "String",
  "availableLicenseCount": 1024,
  "usedLicenseCount": 1024
}
```
