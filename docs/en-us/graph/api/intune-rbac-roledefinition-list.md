<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-rbac-roledefinition-list?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# List roleDefinitions

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

List properties and relationships of the [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) objects.

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
GET /deviceManagement/roleDefinitions
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [roleDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-rbac-roledefinition?view=graph-rest-1.0) objects in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/v1.0/deviceManagement/roleDefinitions
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 746

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.roleDefinition",
      "id": "70fdcd08-cd08-70fd-08cd-fd7008cdfd70",
      "displayName": "Display Name value",
      "description": "Description value",
      "rolePermissions": [
        {
          "@odata.type": "microsoft.graph.rolePermission",
          "resourceActions": [
            {
              "@odata.type": "microsoft.graph.resourceAction",
              "allowedResourceActions": [
                "Allowed Resource Actions value"
              ],
              "notAllowedResourceActions": [
                "Not Allowed Resource Actions value"
              ]
            }
          ]
        }
      ],
      "isBuiltIn": true
    }
  ]
}
```
