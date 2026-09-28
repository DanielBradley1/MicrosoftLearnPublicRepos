<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-androidfotaservice-zebrafotaartifact-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update zebraFotaArtifact

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta) object.

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
PATCH /deviceManagement/zebraFotaArtifacts/{zebraFotaArtifactId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Artifact unique ID from Zebra |
| deviceModel | String | Applicable device model \(e.g.: `TC8300`\) |
| osVersion | String | Artifact OS version \(e.g.: `8.1.0`\) |
| patchVersion | String | Artifact patch version \(e.g.: `U00`\) |
| boardSupportPackageVersion | String | The version of the Board Support Package \(BSP. E.g.: `01.18.02.00`\) |
| releaseNotesUrl | String | Artifact release notes URL \(e.g.: `https://www.zebra.com/<filename.pdf>`\) |
| description | String | Artifact description. \(e.g.: `LifeGuard Update 98 \(released 24-September-2021\) |

## Response

If successful, this method returns a `200 OK` response code and an updated [zebraFotaArtifact](https://learn.microsoft.com/en-us/graph/api/resources/intune-androidfotaservice-zebrafotaartifact?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/zebraFotaArtifacts/{zebraFotaArtifactId}
Content-type: application/json
Content-length: 350

{
  "@odata.type": "#microsoft.graph.zebraFotaArtifact",
  "deviceModel": "Device Model value",
  "osVersion": "Os Version value",
  "patchVersion": "Patch Version value",
  "boardSupportPackageVersion": "Board Support Package Version value",
  "releaseNotesUrl": "https://example.com/releaseNotesUrl/",
  "description": "Description value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 399

{
  "@odata.type": "#microsoft.graph.zebraFotaArtifact",
  "id": "c81cfc78-fc78-c81c-78fc-1cc878fc1cc8",
  "deviceModel": "Device Model value",
  "osVersion": "Os Version value",
  "patchVersion": "Patch Version value",
  "boardSupportPackageVersion": "Board Support Package Version value",
  "releaseNotesUrl": "https://example.com/releaseNotesUrl/",
  "description": "Description value"
}
```
