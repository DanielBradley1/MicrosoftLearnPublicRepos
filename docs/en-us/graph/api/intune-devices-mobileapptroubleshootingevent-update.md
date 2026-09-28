<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-devices-mobileapptroubleshootingevent-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Update mobileAppTroubleshootingEvent

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementManagedDevices.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementManagedDevices.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/mobileAppTroubleshootingEvents/{mobileAppTroubleshootingEventId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object |

## Response

If successful, this method returns a `200 OK` response code and an updated [mobileAppTroubleshootingEvent](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-mobileapptroubleshootingevent?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceManagement/mobileAppTroubleshootingEvents/{mobileAppTroubleshootingEventId}
Content-type: application/json
Content-length: 71

{
  "@odata.type": "#microsoft.graph.mobileAppTroubleshootingEvent"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 120

{
  "@odata.type": "#microsoft.graph.mobileAppTroubleshootingEvent",
  "id": "77943c10-3c10-7794-103c-9477103c9477"
}
```
