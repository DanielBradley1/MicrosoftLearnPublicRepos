<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update endpointPrivilegeManagementProvisioningStatus

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [endpointPrivilegeManagementProvisioningStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus?view=graph-rest-beta) object.

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
PATCH /deviceManagement/endpointPrivilegeManagementProvisioningStatus
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [endpointPrivilegeManagementProvisioningStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [endpointPrivilegeManagementProvisioningStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | A unique identifier represents Intune Account identifier. |
| licenseType | [licenseType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-licensetype?view=graph-rest-beta) | Indicates whether tenant has a valid Intune Endpoint Privilege Management license. Possible value are : 0 - notPaid, 1 - paid, 2 - trial. See LicenseType enum for more details. Default notPaid. Possible values are: `notPaid`, `paid`, `trial`, `unknownFutureValue`. |
| onboardedToMicrosoftManagedPlatform | Boolean | Indicates whether tenant is onboarded to Microsoft Managed Platform - Cloud \(MMPC\). When set to true, implies tenant is onboarded and when set to false, implies tenant is not onboarded. Default set to false. |

## Response

If successful, this method returns a `200 OK` response code and an updated [endpointPrivilegeManagementProvisioningStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-endpointprivilegemanagementprovisioningstatus?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/endpointPrivilegeManagementProvisioningStatus
Content-type: application/json
Content-length: 161

{
  "@odata.type": "#microsoft.graph.endpointPrivilegeManagementProvisioningStatus",
  "licenseType": "paid",
  "onboardedToMicrosoftManagedPlatform": true
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 210

{
  "@odata.type": "#microsoft.graph.endpointPrivilegeManagementProvisioningStatus",
  "id": "49a26797-6797-49a2-9767-a2499767a249",
  "licenseType": "paid",
  "onboardedToMicrosoftManagedPlatform": true
}
```
