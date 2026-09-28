<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-securityconfigurationtask-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create securityConfigurationTask

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
POST /deviceAppManagement/deviceAppManagementTasks
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the securityConfigurationTask object.

The following table shows the properties that are required when you create the securityConfigurationTask.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The entity key. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| displayName | String | The name. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| description | String | The description. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The created date. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| dueDateTime | DateTimeOffset | The due date. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| category | [deviceAppManagementTaskCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskcategory?view=graph-rest-beta) | The category. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta). Possible values are: `unknown`, `advancedThreatProtection`. |
| priority | [deviceAppManagementTaskPriority](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskpriority?view=graph-rest-beta) | The priority. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta). Possible values are: `none`, `high`, `low`. |
| creator | String | The email address of the creator. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| creatorNotes | String | Notes from the creator. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| assignedTo | String | The name or email of the admin this task is assigned to. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) |
| status | [deviceAppManagementTaskStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskstatus?view=graph-rest-beta) | The status. Inherited from [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta). Possible values are: `unknown`, `pending`, `active`, `completed`, `rejected`. |
| endpointSecurityPolicy | [endpointSecurityConfigurationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-endpointsecurityconfigurationtype?view=graph-rest-beta) | The endpoint security policy type. Possible values are: `unknown`, `antivirus`, `diskEncryption`, `firewall`, `endpointDetectionAndResponse`, `attackSurfaceReduction`, `accountProtection`. |
| applicablePlatform | [endpointSecurityConfigurationApplicablePlatform](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-endpointsecurityconfigurationapplicableplatform?view=graph-rest-beta) | The applicable platform. Possible values are: `unknown`, `macOS`, `windows10AndLater`, `windows10AndWindowsServer`. |
| endpointSecurityPolicyProfile | [endpointSecurityConfigurationProfileType](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-endpointsecurityconfigurationprofiletype?view=graph-rest-beta) | The endpoint security policy profile. Possible values are: `unknown`, `antivirus`, `windowsSecurity`, `bitLocker`, `fileVault`, `firewall`, `firewallRules`, `endpointDetectionAndResponse`, `deviceControl`, `appAndBrowserIsolation`, `exploitProtection`, `webProtection`, `applicationControl`, `attackSurfaceReductionRules`, `accountProtection`. |
| insights | String | Information about the mitigation. |
| managedDeviceCount | Int32 | The number of vulnerable devices. |
| intendedSettings | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-keyvaluepair?view=graph-rest-beta) collection | The intended settings and their values. |

## Response

If successful, this method returns a `201 Created` response code and a [securityConfigurationTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-securityconfigurationtask?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceAppManagement/deviceAppManagementTasks
Content-type: application/json
Content-length: 746

{
  "@odata.type": "#microsoft.graph.securityConfigurationTask",
  "displayName": "Display Name value",
  "description": "Description value",
  "dueDateTime": "2017-01-01T00:02:18.1994089-08:00",
  "category": "advancedThreatProtection",
  "priority": "high",
  "creator": "Creator value",
  "creatorNotes": "Creator Notes value",
  "assignedTo": "Assigned To value",
  "status": "pending",
  "endpointSecurityPolicy": "antivirus",
  "applicablePlatform": "macOS",
  "endpointSecurityPolicyProfile": "antivirus",
  "insights": "Insights value",
  "managedDeviceCount": 2,
  "intendedSettings": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "Name value",
      "value": "Value value"
    }
  ]
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 854

{
  "@odata.type": "#microsoft.graph.securityConfigurationTask",
  "id": "5d630f12-0f12-5d63-120f-635d120f635d",
  "displayName": "Display Name value",
  "description": "Description value",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "dueDateTime": "2017-01-01T00:02:18.1994089-08:00",
  "category": "advancedThreatProtection",
  "priority": "high",
  "creator": "Creator value",
  "creatorNotes": "Creator Notes value",
  "assignedTo": "Assigned To value",
  "status": "pending",
  "endpointSecurityPolicy": "antivirus",
  "applicablePlatform": "macOS",
  "endpointSecurityPolicyProfile": "antivirus",
  "insights": "Insights value",
  "managedDeviceCount": 2,
  "intendedSettings": [
    {
      "@odata.type": "microsoft.graph.keyValuePair",
      "name": "Name value",
      "value": "Value value"
    }
  ]
}
```
