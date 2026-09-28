<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-enrollment-enrollmentprofile-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-03-14 -->

# Update enrollmentProfile

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementServiceConfig.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementServiceConfig.ReadWrite.All |

## HTTP Request

```http
PATCH /deviceManagement/depOnboardingSettings/{depOnboardingSettingId}/enrollmentProfiles/{enrollmentProfileId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object |
| displayName | String | Name of the profile |
| description | String | Description of the profile |
| requiresUserAuthentication | Boolean | Indicates if the profile requires user authentication |
| configurationEndpointUrl | String | Configuration endpoint url to use for Enrollment |
| enableAuthenticationViaCompanyPortal | Boolean | Indicates to authenticate with Apple Setup Assistant instead of Company Portal. |
| requireCompanyPortalOnSetupAssistantEnrolledDevices | Boolean | Indicates that Company Portal is required on setup assistant enrolled devices |

## Response

If successful, this method returns a `200 OK` response code and an updated [enrollmentProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-enrollment-enrollmentprofile?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/depOnboardingSettings/{depOnboardingSettingId}/enrollmentProfiles/{enrollmentProfileId}
Content-type: application/json
Content-length: 370

{
  "@odata.type": "#microsoft.graph.enrollmentProfile",
  "displayName": "Display Name value",
  "description": "Description value",
  "requiresUserAuthentication": true,
  "configurationEndpointUrl": "https://example.com/configurationEndpointUrl/",
  "enableAuthenticationViaCompanyPortal": true,
  "requireCompanyPortalOnSetupAssistantEnrolledDevices": true
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 419

{
  "@odata.type": "#microsoft.graph.enrollmentProfile",
  "id": "012d8d5e-8d5e-012d-5e8d-2d015e8d2d01",
  "displayName": "Display Name value",
  "description": "Description value",
  "requiresUserAuthentication": true,
  "configurationEndpointUrl": "https://example.com/configurationEndpointUrl/",
  "enableAuthenticationViaCompanyPortal": true,
  "requireCompanyPortalOnSetupAssistantEnrolledDevices": true
}
```
