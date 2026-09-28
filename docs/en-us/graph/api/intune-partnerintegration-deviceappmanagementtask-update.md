<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-deviceappmanagementtask-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Update deviceAppManagementTask

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) object.

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
PATCH /deviceAppManagement/deviceAppManagementTasks/{deviceAppManagementTaskId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The entity key. |
| displayName | String | The name. |
| description | String | The description. |
| createdDateTime | DateTimeOffset | The created date. |
| dueDateTime | DateTimeOffset | The due date. |
| category | [deviceAppManagementTaskCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskcategory?view=graph-rest-beta) | The category. Possible values are: `unknown`, `advancedThreatProtection`. |
| priority | [deviceAppManagementTaskPriority](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskpriority?view=graph-rest-beta) | The priority. Possible values are: `none`, `high`, `low`. |
| creator | String | The email address of the creator. |
| creatorNotes | String | Notes from the creator. |
| assignedTo | String | The name or email of the admin this task is assigned to. |
| status | [deviceAppManagementTaskStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtaskstatus?view=graph-rest-beta) | The status. Possible values are: `unknown`, `pending`, `active`, `completed`, `rejected`. |

## Response

If successful, this method returns a `200 OK` response code and an updated [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceAppManagement/deviceAppManagementTasks/{deviceAppManagementTaskId}
Content-type: application/json
Content-length: 400

{
  "@odata.type": "#microsoft.graph.deviceAppManagementTask",
  "displayName": "Display Name value",
  "description": "Description value",
  "dueDateTime": "2017-01-01T00:02:18.1994089-08:00",
  "category": "advancedThreatProtection",
  "priority": "high",
  "creator": "Creator value",
  "creatorNotes": "Creator Notes value",
  "assignedTo": "Assigned To value",
  "status": "pending"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 508

{
  "@odata.type": "#microsoft.graph.deviceAppManagementTask",
  "id": "814545cc-45cc-8145-cc45-4581cc454581",
  "displayName": "Display Name value",
  "description": "Description value",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "dueDateTime": "2017-01-01T00:02:18.1994089-08:00",
  "category": "advancedThreatProtection",
  "priority": "high",
  "creator": "Creator value",
  "creatorNotes": "Creator Notes value",
  "assignedTo": "Assigned To value",
  "status": "pending"
}
```
