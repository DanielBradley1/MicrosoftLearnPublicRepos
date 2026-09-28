<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-rbac-operationapprovalpolicy-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# List operationApprovalPolicies

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

List properties and relationships of the [operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta) objects.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementRBAC.Read.All, DeviceManagementRBAC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementRBAC.Read.All, DeviceManagementRBAC.ReadWrite.All |

## HTTP Request

```http
GET /deviceManagement/operationApprovalPolicies
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [operationApprovalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-operationapprovalpolicy?view=graph-rest-beta) objects in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/deviceManagement/operationApprovalPolicies
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 674

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.operationApprovalPolicy",
      "id": "9d2caa5f-aa5f-9d2c-5faa-2c9d5faa2c9d",
      "displayName": "Display Name value",
      "description": "Description value",
      "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
      "policyType": "deviceAction",
      "policyPlatform": "androidDeviceAdministrator",
      "policySet": {
        "@odata.type": "microsoft.graph.operationApprovalPolicySet",
        "policyType": "deviceAction",
        "policyPlatform": "androidDeviceAdministrator"
      },
      "approverGroupIds": [
        "Approver Group Ids value"
      ]
    }
  ]
}
```
