<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceintent-devicemanagementbooleansettinginstance-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create deviceManagementBooleanSettingInstance

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta) object.

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
POST /deviceManagement/intents/{deviceManagementIntentId}/settings
POST /deviceManagement/templates/{deviceManagementTemplateId}/settings
POST /deviceManagement/intents/{deviceManagementIntentId}/categories/{deviceManagementIntentSettingCategoryId}/settings
POST /deviceManagement/templates/{deviceManagementTemplateId}/categories/{deviceManagementTemplateSettingCategoryId}/recommendedSettings
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the deviceManagementBooleanSettingInstance object.

The following table shows the properties that are required when you create the deviceManagementBooleanSettingInstance.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The setting instance ID Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| definitionId | String | The ID of the setting definition for this instance Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| valueJson | String | JSON representation of the value Inherited from [deviceManagementSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementsettinginstance?view=graph-rest-beta) |
| value | Boolean | The boolean value |

## Response

If successful, this method returns a `201 Created` response code and a [deviceManagementBooleanSettingInstance](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceintent-devicemanagementbooleansettinginstance?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/intents/{deviceManagementIntentId}/settings
Content-type: application/json
Content-length: 176

{
  "@odata.type": "#microsoft.graph.deviceManagementBooleanSettingInstance",
  "definitionId": "Definition Id value",
  "valueJson": "Value Json value",
  "value": true
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 225

{
  "@odata.type": "#microsoft.graph.deviceManagementBooleanSettingInstance",
  "id": "bb9b0041-0041-bb9b-4100-9bbb41009bbb",
  "definitionId": "Definition Id value",
  "valueJson": "Value Json value",
  "value": true
}
```
