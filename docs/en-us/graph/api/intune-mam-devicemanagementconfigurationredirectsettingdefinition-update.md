<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-mam-devicemanagementconfigurationredirectsettingdefinition-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# Update deviceManagementConfigurationRedirectSettingDefinition

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta) object.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceAppManagement/targetedManagedAppConfigurations/{targetedManagedAppConfigurationId}/settings/{deviceManagementConfigurationSettingId}/settingDefinitions/{deviceManagementConfigurationSettingDefinitionId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| applicability | [deviceManagementConfigurationSettingApplicability](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingapplicability?view=graph-rest-beta) | Details which device setting is applicable on Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| accessTypes | [deviceManagementConfigurationSettingAccessTypes](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingaccesstypes?view=graph-rest-beta) | Read/write access mode of the setting Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `none`, `add`, `copy`, `delete`, `get`, `replace`, `execute`. |
| keywords | String collection | Tokens which to search settings on Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| infoUrls | String collection | List of links more info for the setting can be found at Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| occurrence | [deviceManagementConfigurationSettingOccurrence](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingoccurrence?view=graph-rest-beta) | Indicates whether the setting is required or not Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| baseUri | String | Base CSP Path Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| offsetUri | String | Offset CSP Path from Base Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| rootDefinitionId | String | Root setting definition if the setting is a child setting. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| categoryId | String | Specifies the area group under which the setting is configured in a specified configuration service provider \(CSP\) Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| settingUsage | [deviceManagementConfigurationSettingUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingusage?view=graph-rest-beta) | Setting type, for example, configuration and compliance Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `none`, `configuration`, `compliance`. |
| uxBehavior | [deviceManagementConfigurationControlType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationcontroltype?view=graph-rest-beta) | Setting control type representation in the UX Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `default`, `dropdown`, `smallTextBox`, `largeTextBox`, `toggle`, `multiheaderGrid`, `contextPane`. |
| visibility | [deviceManagementConfigurationSettingVisibility](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingvisibility?view=graph-rest-beta) | Setting visibility scope to UX Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta). The possible values are: `none`, `settingsCatalog`, `template`. |
| referredSettingInformationList | [deviceManagementConfigurationReferredSettingInformation](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationreferredsettinginformation?view=graph-rest-beta) collection | List of referred setting information. Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| id | String | Identifier for item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| description | String | Description of the item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| helpText | String | Help text of the item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| name | String | Name of the item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| displayName | String | Display name of the item Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| version | String | Item Version Inherited from [deviceManagementConfigurationSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationsettingdefinition?view=graph-rest-beta) |
| deepLink | String | A deep link that points to the specific location in the Intune console where feature support must be managed from. |
| redirectMessage | String | A message that explains that clicking the link will redirect the user to a supported page to manage the settings. |
| redirectReason | String | Indicates the reason for redirecting the user to an alternative location in the console. For example: WiFi profiles are not supported in the settings catalog and must be created with a template policy. |

## Response

If successful, this method returns a `200 OK` response code and an updated [deviceManagementConfigurationRedirectSettingDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementconfigurationredirectsettingdefinition?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceAppManagement/targetedManagedAppConfigurations/{targetedManagedAppConfigurationId}/settings/{deviceManagementConfigurationSettingId}/settingDefinitions/{deviceManagementConfigurationSettingDefinitionId}
Content-type: application/json
Content-length: 1396

{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationRedirectSettingDefinition",
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
  "deepLink": "Deep Link value",
  "redirectMessage": "Redirect Message value",
  "redirectReason": "Redirect Reason value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 1445

{
  "@odata.type": "#microsoft.graph.deviceManagementConfigurationRedirectSettingDefinition",
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
  "referredSettingInformationList": [
    {
      "@odata.type": "microsoft.graph.deviceManagementConfigurationReferredSettingInformation",
      "settingDefinitionId": "Setting Definition Id value"
    }
  ],
  "id": "3e6c3eab-3eab-3e6c-ab3e-6c3eab3e6c3e",
  "description": "Description value",
  "helpText": "Help Text value",
  "name": "Name value",
  "displayName": "Display Name value",
  "version": "Version value",
  "deepLink": "Deep Link value",
  "redirectMessage": "Redirect Message value",
  "redirectReason": "Redirect Reason value"
}
```
