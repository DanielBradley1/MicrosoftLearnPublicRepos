<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-shared-reportroot-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# Update reportRoot

Namespace: microsoft.graph

> **Important:** APIs under the /beta version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-reportroot?view=graph-rest-beta) object. ## Permissions One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from most to least privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) |  |
| **Device configuration** | DeviceManagementConfiguration.ReadWrite.All |
| **Troubleshooting** | DeviceManagementManagedDevices.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application |  |
| **Device configuration** | DeviceManagementConfiguration.ReadWrite.All |
| **Troubleshooting** | DeviceManagementManagedDevices.ReadWrite.All |

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## HTTP Request

```http
PATCH /reports
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-reportroot?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-reportroot?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier for this entity. |

## Response

If successful, this method returns a `200 OK` response code and an updated [reportRoot](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-reportroot?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/reports
Content-type: application/json
Content-length: 2

{}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 101

{
  "@odata.type": "#microsoft.graph.reportRoot",
  "id": "9ab6b3dd-b3dd-9ab6-ddb3-b69addb3b69a"
}
```
