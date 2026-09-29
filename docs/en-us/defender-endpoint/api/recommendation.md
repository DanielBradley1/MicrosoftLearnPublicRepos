<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/recommendation -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Recommendation resource type

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Properties

  


---

| Property | Type | Description |
| --- | --- | --- |
| id | String | Recommendation ID |
| productName | String | Related software name |
| recommendationName | String | Recommendation name |
| Weaknesses | Long | Number of discovered vulnerabilities |
| Vendor | String | Related vendor name |
| recommendedVersion | String | Recommended version |
| recommendedProgram | String | Recommended program |
| recommendedVendor | String | Recommended vendor |
| recommendationCategory | String | Recommendation category. Possible values are: `Accounts`, `Application`, `Network`, `OS`, `SecurityControls` |
| subCategory | String | Recommendation subcategory |
| severityScore | Double | Potential impact of the configuration to the organization's Microsoft Secure Score for Devices \(1-10\) |
| publicExploit | Boolean | Public exploit is available |
| activeAlert | Boolean | Active alert is associated with this recommendation |
| associatedThreats | String collection | Threat analytics report is associated with this recommendation |
| remediationType | String | Remediation type. Possible values are: `ConfigurationChange`,`Update`,`Upgrade`,`Uninstall` |
| Status | Enum | Recommendation exception status. Possible values are: `Active` and `Exception` |
| configScoreImpact | Double | Microsoft Secure Score for Devices impact |
| exposureImpact | Double | Exposure score impact |
| totalMachineCount | Long | Number of installed devices |
| exposedMachinesCount | Long | Number of installed devices that are exposed to vulnerabilities |
| nonProductivityImpactedAssets | Long | Number of devices that aren't affected |
| relatedComponent | String | Related software component |
| exposedCriticalDevices | Numeric | The sum of critical devices in all levels of criticality except "not critical" for a particular recommendation |
