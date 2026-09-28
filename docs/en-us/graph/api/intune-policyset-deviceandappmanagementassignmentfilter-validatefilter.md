<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-policyset-deviceandappmanagementassignmentfilter-validatefilter?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# validateFilter action

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

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
POST /deviceManagement/assignmentFilters/validateFilter
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply JSON representation of the parameters.

The following table shows the parameters that can be used with this action.

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceAndAppManagementAssignmentFilter | [deviceAndAppManagementAssignmentFilter](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-deviceandappmanagementassignmentfilter?view=graph-rest-beta) |  |

## Response

If successful, this action returns a `200 OK` response code and a [assignmentFilterValidationResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-assignmentfiltervalidationresult?view=graph-rest-beta) in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/assignmentFilters/validateFilter

Content-type: application/json
Content-length: 854

{
  "deviceAndAppManagementAssignmentFilter": {
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
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 120

{
  "value": {
    "@odata.type": "microsoft.graph.assignmentFilterValidationResult",
    "isValidRule": true
  }
}
```
