<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-03-18 -->

# Create deviceManagementConfigurationSettingGroupCollectionDefinition

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/reusableSettings
POST /deviceManagement/inventorySettings
POST /deviceManagement/complianceSettings
POST /deviceManagement/configurationSettings
POST /deviceManagement/configurationPolicies/{deviceManagementConfigurationPolicyId}/settings/{deviceManagementConfigurationSettingId}/settingDefinitions
POST /deviceManagement/configurationPolicyTemplates/{deviceManagementConfigurationPolicyTemplateId}/settingTemplates/{deviceManagementConfigurationSettingTemplateId}/settingDefinitions
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the deviceManagementConfigurationSettingGroupCollectionDefinition object.

The following table shows the properties that are required when you create the deviceManagementConfigurationSettingGroupCollectionDefinition.

| Property | Type | Description |
| :--- | :--- | :--- |
| applicability | [deviceManagementConfigurationSettingApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingapplicability?view=graph-rest-beta) | Details which device setting is applicable on. Supports: $filters. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| accessTypes | [deviceManagementConfigurationSettingAccessTypes](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingaccesstypes?view=graph-rest-beta) | Read/write access mode of the setting Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). Possible values are: `none`, `add`, `copy`, `delete`, `get`, `replace`, `execute`. |
| keywords | String collection | Tokens which to search settings on Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| infoUrls | String collection | List of links more info for the setting can be found at. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| occurrence | [deviceManagementConfigurationSettingOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingoccurrence?view=graph-rest-beta) | Indicates whether the setting is required or not Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| baseUri | String | Base CSP Path Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| offsetUri | String | Offset CSP Path from Base Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| rootDefinitionId | String | Root setting definition id if the setting is a child setting. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| categoryId | String | Specify category in which the setting is under. Support $filters. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| settingUsage | [deviceManagementConfigurationSettingUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingusage?view=graph-rest-beta) | Indicate setting type for the setting. Possible values are: configuration, compliance, reusableSetting. Each setting usage has separate API end-point to call. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). Possible values are: `none`, `configuration`, `compliance`, `unknownFutureValue`, `inventory`, `audit`. |
| uxBehavior | [deviceManagementConfigurationControlType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationcontroltype?view=graph-rest-beta) | Setting control type representation in the UX. Possible values are: default, dropdown, smallTextBox, largeTextBox, toggle, multiheaderGrid, contextPane. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). Possible values are: `default`, `dropdown`, `smallTextBox`, `largeTextBox`, `toggle`, `multiheaderGrid`, `contextPane`, `unknownFutureValue`. |
| visibility | [deviceManagementConfigurationSettingVisibility](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingvisibility?view=graph-rest-beta) | Setting visibility scope to UX. Possible values are: none, settingsCatalog, template. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). Possible values are: `none`, `settingsCatalog`, `template`, `unknownFutureValue`, `inventoryCatalog`. |
| riskLevel | [deviceManagementConfigurationSettingRiskLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingrisklevel?view=graph-rest-beta) | Setting risklevel. Possible values are: low, medium, high Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). Possible values are: `low`, `medium`, `high`. |
| referredSettingInformationList | [deviceManagementConfigurationReferredSettingInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationreferredsettinginformation?view=graph-rest-beta) collection | List of referred setting information. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| id | String | Identifier for item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| description | String | Description of the setting. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| helpText | String | Help text of the setting. Give more details of the setting. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| name | String | Name of the item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| displayName | String | Name of the setting. For example: Allow Toast. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| version | String | Item Version Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| childIds | String collection | Dependent child settings to this group of settings. Inherited from [deviceManagementConfigurationSettingGroupDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupdefinition?view=graph-rest-beta) |
| dependentOn | [deviceManagementConfigurationDependentOn](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationdependenton?view=graph-rest-beta) collection | List of Dependencies for the setting group Inherited from [deviceManagementConfigurationSettingGroupDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupdefinition?view=graph-rest-beta) |
| dependedOnBy | [deviceManagementConfigurationSettingDependedOnBy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettingdependedonby?view=graph-rest-beta) collection | List of child settings that depend on this setting Inherited from [deviceManagementConfigurationSettingGroupDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupdefinition?view=graph-rest-beta) |
| maximumCount | Int32 | Maximum number of setting group count in the collection. Valid values 1 to 100 |
| minimumCount | Int32 | Minimum number of setting group count in the collection. Valid values 1 to 100 |

## Response

If successful, this method returns a `201 Created` response code and a [deviceManagementConfigurationSettingGroupCollectionDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementconfigurationsettinggroupcollectiondefinition?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/reusableSettings
Content-type: application/json
Content-length: 1813

{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSettingGroupCollectionDefinition",
  "applicability": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingApplicability",
    "description": "Description value",
    "platform": "android",
    "deviceMode": "kiosk",
    "technologies": "mdm"
  },
  "accessTypes": "add",
  "keywords": [
    "Keywords value"
  ],
  "infoUrls": [
    "Info Urls value"
  ],
  "occurrence": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingOccurrence",
    "minDeviceOccurrence": 3,
    "maxDeviceOccurrence": 3
  },
  "baseUri": "Base Uri value",
  "offsetUri": "Offset Uri value",
  "rootDefinitionId": "Root Definition Id value",
  "categoryId": "Category Id value",
  "settingUsage": "configuration",
  "uxBehavior": "dropdown",
  "visibility": "settingsCatalog",
  "riskLevel": "medium",
  "referredSettingInformationList": [
    {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationReferredSettingInformation",
      "settingDefinitionId": "Setting Definition Id value"
    }
  ],
  "description": "Description value",
  "helpText": "Help Text value",
  "name": "Name value",
  "displayName": "Display Name value",
  "version": "Version value",
  "childIds": [
    "Child Ids value"
  ],
  "dependentOn": [
    {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationDependentOn",
      "dependentOn": "Dependent On value",
      "parentSettingId": "Parent Setting Id value"
    }
  ],
  "dependedOnBy": [
    {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingDependedOnBy",
      "dependedOnBy": "Depended On By value",
      "required": true
    }
  ],
  "maximumCount": 12,
  "minimumCount": 12
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 1862

{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationSettingGroupCollectionDefinition",
  "applicability": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingApplicability",
    "description": "Description value",
    "platform": "android",
    "deviceMode": "kiosk",
    "technologies": "mdm"
  },
  "accessTypes": "add",
  "keywords": [
    "Keywords value"
  ],
  "infoUrls": [
    "Info Urls value"
  ],
  "occurrence": {
    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingOccurrence",
    "minDeviceOccurrence": 3,
    "maxDeviceOccurrence": 3
  },
  "baseUri": "Base Uri value",
  "offsetUri": "Offset Uri value",
  "rootDefinitionId": "Root Definition Id value",
  "categoryId": "Category Id value",
  "settingUsage": "configuration",
  "uxBehavior": "dropdown",
  "visibility": "settingsCatalog",
  "riskLevel": "medium",
  "referredSettingInformationList": [
    {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationReferredSettingInformation",
      "settingDefinitionId": "Setting Definition Id value"
    }
  ],
  "id": "739da194-a194-739d-94a1-9d7394a19d73",
  "description": "Description value",
  "helpText": "Help Text value",
  "name": "Name value",
  "displayName": "Display Name value",
  "version": "Version value",
  "childIds": [
    "Child Ids value"
  ],
  "dependentOn": [
    {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationDependentOn",
      "dependentOn": "Dependent On value",
      "parentSettingId": "Parent Setting Id value"
    }
  ],
  "dependedOnBy": [
    {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingDependedOnBy",
      "dependedOnBy": "Depended On By value",
      "required": true
    }
  ],
  "maximumCount": 12,
  "minimumCount": 12
}
```
