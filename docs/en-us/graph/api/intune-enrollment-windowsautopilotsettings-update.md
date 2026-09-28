<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-enrollment-windowsautopilotsettings-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update windowsAutopilotSettings

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [windowsAutopilotSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotsettings?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementServiceConfig.ReadWrite.All, DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementServiceConfig.ReadWrite.All, DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/windowsAutopilotSettings
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [windowsAutopilotSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotsettings?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [windowsAutopilotSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotsettings?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object |
| lastSyncDateTime | DateTimeOffset | Last data sync date time with DDS service. |
| lastManualSyncTriggerDateTime | DateTimeOffset | Last data sync date time with DDS service. |
| syncStatus | [windowsAutopilotSyncStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotsyncstatus?view=graph-rest-beta) | Indicates the status of sync with Device data sync \(DDS\) service. Possible values are: `unknown`, `inProgress`, `completed`, `failed`. |

## Response

If successful, this method returns a `200 OK` response code and an updated [windowsAutopilotSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-windowsautopilotsettings?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/windowsAutopilotSettings
Content-type: application/json
Content-length: 230

{
  "@odata.type": "#microsoft.graph.windowsAutopilotSettings",
  "lastSyncDateTime": "2017-01-01T00:02:49.3205976-08:00",
  "lastManualSyncTriggerDateTime": "2016-12-31T23:57:54.7364636-08:00",
  "syncStatus": "inProgress"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 279

{
  "@odata.type": "#microsoft.graph.windowsAutopilotSettings",
  "id": "08c16770-6770-08c1-7067-c1087067c108",
  "lastSyncDateTime": "2017-01-01T00:02:49.3205976-08:00",
  "lastManualSyncTriggerDateTime": "2016-12-31T23:57:54.7364636-08:00",
  "syncStatus": "inProgress"
}
```
