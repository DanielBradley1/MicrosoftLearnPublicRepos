<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-securitybaselinetemplate-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create securityBaselineTemplate

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta) object.

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
POST /deviceManagement/templates
POST /deviceManagement/templates/{deviceManagementTemplateId}/migratableTo
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the securityBaselineTemplate object.

The following table shows the properties that are required when you create the securityBaselineTemplate.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The template ID Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| displayName | String | The template's display name Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| description | String | The template's description Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| versionInfo | String | The template's version information Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| isDeprecated | Boolean | The template is deprecated or not. Intents cannot be created from a deprecated template. Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| intentCount | Int32 | Number of Intents created from this template. Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |
| templateType | [deviceManagementTemplateType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatetype?view=graph-rest-beta) | The template's type. Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta). Possible values are: `securityBaseline`, `specializedDevices`, `advancedThreatProtectionSecurityBaseline`, `deviceConfiguration`, `custom`, `securityTemplate`, `microsoftEdgeSecurityBaseline`, `microsoftOffice365ProPlusSecurityBaseline`, `deviceCompliance`, `deviceConfigurationForOffice365`, `cloudPC`, `firewallSharedSettings`. |
| platformType | [policyPlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-policyplatformtype?view=graph-rest-beta) | The template's platform. Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta). Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `windows10XProfile`, `linux`, `all`. |
| templateSubtype | [deviceManagementTemplateSubtype](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplatesubtype?view=graph-rest-beta) | The template's subtype. Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta). Possible values are: `none`, `firewall`, `diskEncryption`, `attackSurfaceReduction`, `endpointDetectionReponse`, `accountProtection`, `antivirus`, `firewallSharedAppList`, `firewallSharedIpList`, `firewallSharedPortlist`. |
| publishedDateTime | DateTimeOffset | When the template was published Inherited from [deviceManagementTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementtemplate?view=graph-rest-beta) |

## Response

If successful, this method returns a `201 Created` response code and a [securityBaselineTemplate](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-securitybaselinetemplate?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/templates
Content-type: application/json
Content-length: 405

{
  "@odata.type": "#microsoft.graph.securityBaselineTemplate",
  "displayName": "Display Name value",
  "description": "Description value",
  "versionInfo": "Version Info value",
  "isDeprecated": true,
  "intentCount": 11,
  "templateType": "specializedDevices",
  "platformType": "androidForWork",
  "templateSubtype": "firewall",
  "publishedDateTime": "2016-12-31T23:58:16.1180489-08:00"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 454

{
  "@odata.type": "#microsoft.graph.securityBaselineTemplate",
  "id": "3f61d4c2-d4c2-3f61-c2d4-613fc2d4613f",
  "displayName": "Display Name value",
  "description": "Description value",
  "versionInfo": "Version Info value",
  "isDeprecated": true,
  "intentCount": 11,
  "templateType": "specializedDevices",
  "platformType": "androidForWork",
  "templateSubtype": "firewall",
  "publishedDateTime": "2016-12-31T23:58:16.1180489-08:00"
}
```
