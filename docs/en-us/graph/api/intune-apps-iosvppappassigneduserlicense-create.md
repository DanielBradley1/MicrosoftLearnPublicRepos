<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-apps-iosvppappassigneduserlicense-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Create iosVppAppAssignedUserLicense

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.ReadWrite.All, DeviceManagementApps.ReadWrite.All |

## HTTP Request

```http
POST /deviceAppManagement/mobileApps/{mobileAppId}/microsoft.graph.iosVppApp/assignedLicenses
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the iosVppAppAssignedUserLicense object.

The following table shows the properties that are required when you create the iosVppAppAssignedUserLicense.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. This property is read-only. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userEmailAddress | String | The user email address. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userId | String | The user ID. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userName | String | The user name. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |
| userPrincipalName | String | The user principal name. Inherited from [iosVppAppAssignedLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassignedlicense?view=graph-rest-beta) |

## Response

If successful, this method returns a `201 Created` response code and a [iosVppAppAssignedUserLicense](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-iosvppappassigneduserlicense?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceAppManagement/mobileApps/{mobileAppId}/microsoft.graph.iosVppApp/assignedLicenses
Content-type: application/json
Content-length: 238

{
  "@odata.type": "#microsoft.graph.iosVppAppAssignedUserLicense",
  "userEmailAddress": "User Email Address value",
  "userId": "User Id value",
  "userName": "User Name value",
  "userPrincipalName": "User Principal Name value"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 287

{
  "@odata.type": "#microsoft.graph.iosVppAppAssignedUserLicense",
  "id": "fedc747d-747d-fedc-7d74-dcfe7d74dcfe",
  "userEmailAddress": "User Email Address value",
  "userId": "User Id value",
  "userName": "User Name value",
  "userPrincipalName": "User Principal Name value"
}
```
