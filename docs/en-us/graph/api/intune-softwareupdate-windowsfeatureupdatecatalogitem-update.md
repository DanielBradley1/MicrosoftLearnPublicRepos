<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsfeatureupdatecatalogitem-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update windowsFeatureUpdateCatalogItem

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta) object.

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
PATCH /deviceManagement/windowsUpdateCatalogItems/{windowsUpdateCatalogItemId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The catalog item id. Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| displayName | String | The display name for the catalog item. Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| releaseDateTime | DateTimeOffset | The date the catalog item was released Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| endOfSupportDate | DateTimeOffset | The last supported date for a catalog item Inherited from [windowsUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsupdatecatalogitem?view=graph-rest-beta) |
| version | String | The feature update version |

## Response

If successful, this method returns a `200 OK` response code and an updated [windowsFeatureUpdateCatalogItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsfeatureupdatecatalogitem?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/windowsUpdateCatalogItems/{windowsUpdateCatalogItemId}
Content-type: application/json
Content-length: 263

{
  "@odata.type": "#microsoft.graph.windowsFeatureUpdateCatalogItem",
  "displayName": "Display Name value",
  "releaseDateTime": "2017-01-01T00:01:34.7470482-08:00",
  "endOfSupportDate": "2017-01-01T00:02:08.3437725-08:00",
  "version": "Version value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 312

{
  "@odata.type": "#microsoft.graph.windowsFeatureUpdateCatalogItem",
  "id": "cbd85729-5729-cbd8-2957-d8cb2957d8cb",
  "displayName": "Display Name value",
  "releaseDateTime": "2017-01-01T00:01:34.7470482-08:00",
  "endOfSupportDate": "2017-01-01T00:02:08.3437725-08:00",
  "version": "Version value"
}
```
