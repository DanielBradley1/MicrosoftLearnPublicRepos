<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-shared-deviceenrollmentconfiguration-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-10 -->

# List deviceEnrollmentConfigurations

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

List properties and relationships of the [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) objects.

```
    ## Permissions
```

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from most to least privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementServiceConfig.Read.All, DeviceManagementServiceConfig.ReadWrite.All |
| **Onboarding** | DeviceManagementServiceConfig.ReadWrite.All, DeviceManagementServiceConfig.Read.All |
| **Policy Set** | DeviceManagementServiceConfig.ReadWrite.All, DeviceManagementServiceConfig.Read.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementServiceConfig.Read.All, DeviceManagementServiceConfig.ReadWrite.All |
| **Onboarding** | DeviceManagementServiceConfig.ReadWrite.All, DeviceManagementServiceConfig.Read.All |
| **Policy Set** | DeviceManagementServiceConfig.ReadWrite.All, DeviceManagementServiceConfig.Read.All |

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## HTTP Request

```http
GET /deviceManagement/deviceEnrollmentConfigurations
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [deviceEnrollmentConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceenrollmentconfiguration?view=graph-rest-beta) objects in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/deviceManagement/deviceEnrollmentConfigurations
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 422

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.deviceEnrollmentConfiguration",
      "id": "df13d8b9-d8b9-df13-b9d8-13dfb9d813df",
      "displayName": "Display Name value",
      "description": "Description value",
      "priority": 8,
      "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
      "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
      "version": 7
    }
  ]
}
```
