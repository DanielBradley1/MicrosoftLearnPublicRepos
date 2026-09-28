<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-onboarding-organization-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Update organization

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [organization](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-organization?view=graph-rest-1.0) object.

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
PATCH /organization/{organizationId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [organization](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-organization?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [organization](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-organization?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The GUID for the object. |
| mobileDeviceManagementAuthority | [mdmAuthority](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mdmauthority?view=graph-rest-1.0) | Mobile device management authority. The possible values are: `unknown`, `intune`, `sccm`, `office365`. |

## Response

If successful, this method returns a `200 OK` response code and an updated [organization](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-organization?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/organization/{organizationId}
Content-type: application/json
Content-length: 102

{
  "@odata.type": "#microsoft.graph.organization",
  "mobileDeviceManagementAuthority": "intune"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 151

{
  "@odata.type": "#microsoft.graph.organization",
  "id": "9efe224a-224a-9efe-4a22-fe9e4a22fe9e",
  "mobileDeviceManagementAuthority": "intune"
}
```
