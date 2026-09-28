<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-remoteassistance-remoteassistancesettings-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update remoteAssistanceSettings

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [remoteAssistanceSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancesettings?view=graph-rest-beta) object.

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
PATCH /deviceManagement/remoteAssistanceSettings
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [remoteAssistanceSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancesettings?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [remoteAssistanceSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancesettings?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The remote assistance settings identifier |
| remoteAssistanceState | [remoteAssistanceState](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancestate?view=graph-rest-beta) | The current state of remote assistance for the account. Possible values are: disabled, enabled. This setting is configurable by the admin. Remote assistance settings that have not yet been configured by the admin have a disabled state. Returned by default. Possible values are: `disabled`, `enabled`. |
| allowSessionsToUnenrolledDevices | Boolean | Indicates if sessions to unenrolled devices are allowed for the account. This setting is configurable by the admin. Default value is false. |
| blockChat | Boolean | Indicates if sessions to block chat function. This setting is configurable by the admin. Default value is false. |

## Response

If successful, this method returns a `200 OK` response code and an updated [remoteAssistanceSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-remoteassistance-remoteassistancesettings?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/remoteAssistanceSettings
Content-type: application/json
Content-length: 172

{
  "@odata.type": "#microsoft.graph.remoteAssistanceSettings",
  "remoteAssistanceState": "enabled",
  "allowSessionsToUnenrolledDevices": true,
  "blockChat": true
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 221

{
  "@odata.type": "#microsoft.graph.remoteAssistanceSettings",
  "id": "cfef360e-360e-cfef-0e36-efcf0e36efcf",
  "remoteAssistanceState": "enabled",
  "allowSessionsToUnenrolledDevices": true,
  "blockChat": true
}
```
