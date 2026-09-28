<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-rbac-resourceoperation-create?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Create resourceOperation

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementRBAC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementRBAC.ReadWrite.All |

## HTTP Request

```http
POST /deviceManagement/resourceOperations
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the resourceOperation object.

The following table shows the properties that are required when you create the resourceOperation.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the Resource Operation. Read-only, automatically generated. |
| resourceName | String | Name of the Resource this operation is performed on. |
| actionName | String | Type of action this operation is going to perform. The actionName should be concise and limited to as few words as possible. |
| description | String | Description of the resource operation. The description is used in mouse-over text for the operation when shown in the Azure Portal. |

## Response

If successful, this method returns a `201 Created` response code and a [resourceOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-resourceoperation?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/v1.0/deviceManagement/resourceOperations
Content-type: application/json
Content-length: 178

{
  "@odata.type": "#microsoft.graph.resourceOperation",
  "resourceName": "Resource Name value",
  "actionName": "Action Name value",
  "description": "Description value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 227

{
  "@odata.type": "#microsoft.graph.resourceOperation",
  "id": "232b8fee-8fee-232b-ee8f-2b23ee8f2b23",
  "resourceName": "Resource Name value",
  "actionName": "Action Name value",
  "description": "Description value"
}
```
