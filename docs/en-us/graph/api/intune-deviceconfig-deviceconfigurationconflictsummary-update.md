<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-deviceconfigurationconflictsummary-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update deviceConfigurationConflictSummary

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/deviceConfigurationConflictSummary/{deviceConfigurationConflictSummaryId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| conflictingDeviceConfigurations | [settingSource](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-settingsource?view=graph-rest-beta) collection | The set of policies in conflict with the given setting |
| id | String | The id for this set of conflicting policies. This id is the ids of all the policies in ConflictingDeviceConfigurations in lexicographical order separated by underscores. |
| contributingSettings | String collection | The set of settings in conflict with the given policies |
| deviceCheckinsImpacted | Int32 | The count of checkins impacted by the conflicting policies and settings |

## Response

If successful, this method returns a `200 OK` response code and an updated [deviceConfigurationConflictSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceconfigurationconflictsummary?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/deviceConfigurationConflictSummary/{deviceConfigurationConflictSummaryId}
Content-type: application/json
Content-length: 398

{
  "@odata.type": "#microsoft.graph.deviceConfigurationConflictSummary",
  "conflictingDeviceConfigurations": [
    {
      "@odata.type": "microsoft.graph.settingSource",
      "id": "Id value",
      "displayName": "Display Name value",
      "sourceType": "deviceIntent"
    }
  ],
  "contributingSettings": [
    "Contributing Settings value"
  ],
  "deviceCheckinsImpacted": 6
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 447

{
  "@odata.type": "#microsoft.graph.deviceConfigurationConflictSummary",
  "conflictingDeviceConfigurations": [
    {
      "@odata.type": "microsoft.graph.settingSource",
      "id": "Id value",
      "displayName": "Display Name value",
      "sourceType": "deviceIntent"
    }
  ],
  "id": "d5f22c23-2c23-d5f2-232c-f2d5232cf2d5",
  "contributingSettings": [
    "Contributing Settings value"
  ],
  "deviceCheckinsImpacted": 6
}
```
