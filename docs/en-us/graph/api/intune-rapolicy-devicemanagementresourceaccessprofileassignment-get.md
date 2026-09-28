<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementresourceaccessprofileassignment-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Get deviceManagementResourceAccessProfileAssignment

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Read properties and relationships of the [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementServiceConfig.Read.All, DeviceManagementServiceConfig.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementServiceConfig.Read.All, DeviceManagementServiceConfig.ReadWrite.All |

## HTTP Request

```http
GET /deviceManagement/resourceAccessProfiles/{deviceManagementResourceAccessProfileBaseId}/assignments/{deviceManagementResourceAccessProfileAssignmentId}
```

## Optional query parameters

This method supports the [OData Query Parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/deviceManagement/resourceAccessProfiles/{deviceManagementResourceAccessProfileBaseId}/assignments/{deviceManagementResourceAccessProfileAssignmentId}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 566

{
  "value": {
    "@odata.type": "#microsoft.graph.deviceManagementResourceAccessProfileAssignment",
    "id": "4ebb8d4e-8d4e-4ebb-4e8d-bb4e4e8dbb4e",
    "intent": "remove",
    "target": {
      "@odata.type": "microsoft.graph.scopeTagGroupAssignmentTarget",
      "deviceAndAppManagementAssignmentFilterId": "Device And App Management Assignment Filter Id value",
      "deviceAndAppManagementAssignmentFilterType": "include",
      "targetType": "user",
      "entraObjectId": "Entra Object Id value"
    },
    "sourceId": "Source Id value"
  }
}
```
