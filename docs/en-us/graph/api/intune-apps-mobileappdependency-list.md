<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-apps-mobileappdependency-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# List mobileAppDependencies

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

List properties and relationships of the [mobileAppDependency](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappdependency?view=graph-rest-beta) objects.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementApps.Read.All, DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementApps.Read.All, DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
GET /deviceAppManagement/mobileAppRelationships
GET /deviceAppManagement/mobileApps/{mobileAppId}/relationships
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [mobileAppDependency](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappdependency?view=graph-rest-beta) objects in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/deviceAppManagement/mobileAppRelationships
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 804

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.mobileAppDependency",
      "id": "c7f6f9ab-f9ab-c7f6-abf9-f6c7abf9f6c7",
      "targetId": "Target Id value",
      "targetDisplayName": "Target Display Name value",
      "targetDisplayVersion": "Target Display Version value",
      "targetPublisher": "Target Publisher value",
      "targetPublisherDisplayName": "Target Publisher Display Name value",
      "sourceId": "Source Id value",
      "sourceDisplayName": "Source Display Name value",
      "sourceDisplayVersion": "Source Display Version value",
      "sourcePublisherDisplayName": "Source Publisher Display Name value",
      "targetType": "parent",
      "dependencyType": "autoInstall",
      "dependentAppCount": 1,
      "dependsOnAppCount": 1
    }
  ]
}
```
