<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-shared-user-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-01 -->

# Update user

Namespace: microsoft.graph

> **Important:** APIs under the /beta version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) object.

```
    ## Permissions
```

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from most to least privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) |  |
| **Device management** | DeviceManagementManagedDevices.ReadWrite.All |
| **MAM** | DeviceManagementApps.ReadWrite.All |
| **Onboarding** | DeviceManagementServiceConfig.ReadWrite.All |
| **Troubleshooting** | DeviceManagementManagedDevices.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application |  |
| **Device management** | DeviceManagementManagedDevices.ReadWrite.All |
| **MAM** | DeviceManagementApps.ReadWrite.All |
| **Onboarding** | DeviceManagementServiceConfig.ReadWrite.All |
| **Troubleshooting** | DeviceManagementManagedDevices.ReadWrite.All |

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## HTTP Request

```http
PATCH /users/{usersId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier of the user. |
| **Onboarding** |  |  |
| deviceEnrollmentLimit | Int32 | The limit on the maximum number of devices that the user is permitted to enroll. Allowed values are 5 or 1000. |

## Response

If successful, this method returns a `200 OK` response code and an updated [user](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-user?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/users/{usersId}
Content-type: application/json
Content-length: 2

{}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 95

{
  "@odata.type": "#microsoft.graph.user",
  "id": "d36894ae-94ae-d368-ae94-68d3ae9468d3"
}
```
