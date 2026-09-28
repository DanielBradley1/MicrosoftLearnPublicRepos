<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-unsupportedgrouppolicyextension-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Update unsupportedGroupPolicyExtension

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) object.

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
PATCH /deviceManagement/groupPolicyMigrationReports/{groupPolicyMigrationReportId}/unsupportedGroupPolicyExtensions/{unsupportedGroupPolicyExtensionId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |
| settingScope | [groupPolicySettingScope](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingscope?view=graph-rest-beta) | Setting Scope of the unsupported extension. Possible values are: `unknown`, `device`, `user`. |
| namespaceUrl | String | Namespace Url of the unsupported extension. |
| extensionType | String | ExtensionType of the unsupported extension. |
| nodeName | String | Node name of the unsupported extension. |

## Response

If successful, this method returns a `200 OK` response code and an updated [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/groupPolicyMigrationReports/{groupPolicyMigrationReportId}/unsupportedGroupPolicyExtensions/{unsupportedGroupPolicyExtensionId}
Content-type: application/json
Content-length: 236

{
  "@odata.type": "#microsoft.graph.unsupportedGroupPolicyExtension",
  "settingScope": "device",
  "namespaceUrl": "https://example.com/namespaceUrl/",
  "extensionType": "Extension Type value",
  "nodeName": "Node Name value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 285

{
  "@odata.type": "#microsoft.graph.unsupportedGroupPolicyExtension",
  "id": "e59ecce2-cce2-e59e-e2cc-9ee5e2cc9ee5",
  "settingScope": "device",
  "namespaceUrl": "https://example.com/namespaceUrl/",
  "extensionType": "Extension Type value",
  "nodeName": "Node Name value"
}
```
