<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-partnerintegration-configmanagercollection-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update configManagerCollection

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta) object.

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
PATCH /deviceManagement/configManagerCollections/{configManagerCollectionId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The key for the ConfigManager Collection. |
| displayName | String | The DisplayName. |
| collectionIdentifier | String | The collection identifier in SCCM. |
| hierarchyName | String | The HierarchyName. |
| hierarchyIdentifier | String | The Hierarchy Identifier. |
| createdDateTime | DateTimeOffset | The created date. |
| lastModifiedDateTime | DateTimeOffset | The last modified date. |

## Response

If successful, this method returns a `200 OK` response code and an updated [configManagerCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-configmanagercollection?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/configManagerCollections/{configManagerCollectionId}
Content-type: application/json
Content-length: 263

{
  "@odata.type": "#microsoft.graph.configManagerCollection",
  "displayName": "Display Name value",
  "collectionIdentifier": "Collection Identifier value",
  "hierarchyName": "Hierarchy Name value",
  "hierarchyIdentifier": "Hierarchy Identifier value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 435

{
  "@odata.type": "#microsoft.graph.configManagerCollection",
  "id": "5f9d1d76-1d76-5f9d-761d-9d5f761d9d5f",
  "displayName": "Display Name value",
  "collectionIdentifier": "Collection Identifier value",
  "hierarchyName": "Hierarchy Name value",
  "hierarchyIdentifier": "Hierarchy Identifier value",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00"
}
```
