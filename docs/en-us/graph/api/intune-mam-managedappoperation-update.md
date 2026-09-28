<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-mam-managedappoperation-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Update managedAppOperation

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceAppManagement/managedAppRegistrations/{managedAppRegistrationId}/operations/{managedAppOperationId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The operation name. |
| lastModifiedDateTime | DateTimeOffset | The last time the app operation was modified. |
| state | String | The current state of the operation |
| id | String | Key of the entity. |
| version | String | Version of the entity. |

## Response

If successful, this method returns a `200 OK` response code and an updated [managedAppOperation](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappoperation?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceAppManagement/managedAppRegistrations/{managedAppRegistrationId}/operations/{managedAppOperationId}
Content-type: application/json
Content-length: 159

{
  "@odata.type": "#microsoft.graph.managedAppOperation",
  "displayName": "Display Name value",
  "state": "State value",
  "version": "Version value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 272

{
  "@odata.type": "#microsoft.graph.managedAppOperation",
  "displayName": "Display Name value",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "state": "State value",
  "id": "f2867b06-7b06-f286-067b-86f2067b86f2",
  "version": "Version value"
}
```
