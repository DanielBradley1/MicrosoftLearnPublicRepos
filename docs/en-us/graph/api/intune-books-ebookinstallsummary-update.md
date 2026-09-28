<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-books-ebookinstallsummary-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Update eBookInstallSummary

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary?view=graph-rest-1.0) object.

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
PATCH /deviceAppManagement/managedEBooks/{managedEBookId}/installSummary
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| installedDeviceCount | Int32 | Number of Devices that have successfully installed this book. |
| failedDeviceCount | Int32 | Number of Devices that have failed to install this book. |
| notInstalledDeviceCount | Int32 | Number of Devices that does not have this book installed. |
| installedUserCount | Int32 | Number of Users whose devices have all succeeded to install this book. |
| failedUserCount | Int32 | Number of Users that have 1 or more device that failed to install this book. |
| notInstalledUserCount | Int32 | Number of Users that did not install this book. |

## Response

If successful, this method returns a `200 OK` response code and an updated [eBookInstallSummary](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-ebookinstallsummary?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceAppManagement/managedEBooks/{managedEBookId}/installSummary
Content-type: application/json
Content-length: 236

{
  "@odata.type": "#microsoft.graph.eBookInstallSummary",
  "installedDeviceCount": 4,
  "failedDeviceCount": 1,
  "notInstalledDeviceCount": 7,
  "installedUserCount": 2,
  "failedUserCount": 15,
  "notInstalledUserCount": 5
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 285

{
  "@odata.type": "#microsoft.graph.eBookInstallSummary",
  "id": "9708ad78-ad78-9708-78ad-089778ad0897",
  "installedDeviceCount": 4,
  "failedDeviceCount": 1,
  "notInstalledDeviceCount": 7,
  "installedUserCount": 2,
  "failedUserCount": 15,
  "notInstalledUserCount": 5
}
```
