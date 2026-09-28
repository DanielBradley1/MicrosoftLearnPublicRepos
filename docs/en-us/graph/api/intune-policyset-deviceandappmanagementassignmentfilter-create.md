<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create deviceAndAppManagementAssignmentFilter

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) object.

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
POST /deviceManagement/assignmentFilters
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the deviceAndAppManagementAssignmentFilter object.

The following table shows the properties that are required when you create the deviceAndAppManagementAssignmentFilter.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the Assignment Filter. |
| createdDateTime | DateTimeOffset | The creation time of the assignment filter. The value cannot be modified and is automatically populated during new assignment filter process. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z'. |
| lastModifiedDateTime | DateTimeOffset | Last modified time of the Assignment Filter. The timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 would look like this: '2014-01-01T00:00:00Z' |
| displayName | String | The name of the Assignment Filter. |
| description | String | Optional description of the Assignment Filter. |
| platform | [devicePlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceplatformtype?view=graph-rest-beta) | Indicates filter is applied to which flatform. Possible values are android,androidForWork,iOS,macOS,windowsPhone81,windows81AndLater,windows10AndLater,androidWorkProfile, unknown, androidAOSP, androidMobileApplicationManagement, iOSMobileApplicationManagement, windowsMobileApplicationManagement. Default filter will be applied to 'unknown'. Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidAOSP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`, `windowsMobileApplicationManagement`. |
| rule | String | Rule definition of the assignment filter. |
| roleScopeTags | String collection | Indicates role scope tags assigned for the assignment filter. |
| payloads | [payloadByFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-payloadbyfilter?view=graph-rest-beta) collection | Indicates associated assignments for a specific filter. |
| assignmentFilterManagementType | [assignmentFilterManagementType](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfiltermanagementtype?view=graph-rest-beta) | Indicates filter is applied to either 'devices' or 'apps' management type. Possible values are devices, apps. Default filter will be applied to 'devices'. Possible values are: `devices`, `apps`, `unknownFutureValue`. |

## Response

If successful, this method returns a `201 Created` response code and a [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/assignmentFilters
Content-type: application/json
Content-length: 588

{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementAssignmentFilter",
  "displayName": "Display Name value",
  "description": "Description value",
  "platform": "androidForWork",
  "rule": "Rule value",
  "roleScopeTags": [
    "Role Scope Tags value"
  ],
  "payloads": [
    {
      "@odata.type": "microsoft.graph.payloadByFilter",
      "payloadId": "Payload Id value",
      "payloadType": "deviceConfigurationAndCompliance",
      "groupId": "Group Id value",
      "assignmentFilterType": "include"
    }
  ],
  "assignmentFilterManagementType": "apps"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 760

{
  "@odata.type": "#microsoft.graph.deviceAndAppManagementAssignmentFilter",
  "id": "819818db-18db-8198-db18-9881db189881",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "displayName": "Display Name value",
  "description": "Description value",
  "platform": "androidForWork",
  "rule": "Rule value",
  "roleScopeTags": [
    "Role Scope Tags value"
  ],
  "payloads": [
    {
      "@odata.type": "microsoft.graph.payloadByFilter",
      "payloadId": "Payload Id value",
      "payloadType": "deviceConfigurationAndCompliance",
      "groupId": "Group Id value",
      "assignmentFilterType": "include"
    }
  ],
  "assignmentFilterManagementType": "apps"
}
```
