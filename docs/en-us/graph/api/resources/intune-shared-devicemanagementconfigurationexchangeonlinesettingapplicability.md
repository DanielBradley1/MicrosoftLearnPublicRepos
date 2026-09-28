<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationexchangeonlinesettingapplicability?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementConfigurationExchangeOnlineSettingApplicability resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Applicability for an Exchange Online Setting

Inherits from [deviceManagementConfigurationSettingApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingapplicability?view=graph-rest-beta)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | description of the setting Inherited from [deviceManagementConfigurationSettingApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingapplicability?view=graph-rest-beta) |
| platform | [deviceManagementConfigurationPlatforms](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationplatforms?view=graph-rest-beta) | Platform setting can be applied on Inherited from [deviceManagementConfigurationSettingApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingapplicability?view=graph-rest-beta). The possible values are: `none`, `android`, `iOS`, `macOS`, `windows10X`, `windows10`, `linux`, `unknownFutureValue`. |
| deviceMode | [deviceManagementConfigurationDeviceMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationdevicemode?view=graph-rest-beta) | Device Mode that setting can be applied on Inherited from [deviceManagementConfigurationSettingApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingapplicability?view=graph-rest-beta). The possible values are: `none`, `kiosk`. |
| technologies | [deviceManagementConfigurationTechnologies](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationtechnologies?view=graph-rest-beta) | Which technology channels this setting can be deployed through Inherited from [deviceManagementConfigurationSettingApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingapplicability?view=graph-rest-beta). The possible values are: `none`, `mdm`, `windows10XManagement`, `configManager`, `appleRemoteManagement`, `microsoftSense`, `exchangeOnline`, `linuxMdm`, `enrollment`, `endpointPrivilegeManagement`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationExchangeOnlineSettingApplicability",
  "description": "String",
  "platform": "String",
  "deviceMode": "String",
  "technologies": "String"
}
```
