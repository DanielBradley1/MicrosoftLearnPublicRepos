<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windows81compliancepolicy-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Update windows81CompliancePolicy

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [windows81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81compliancepolicy?view=graph-rest-1.0) object.

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
PATCH /deviceManagement/deviceCompliancePolicies/{deviceCompliancePolicyId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [windows81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81compliancepolicy?view=graph-rest-1.0) object.

The following table shows the properties that are required when you create the [windows81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81compliancepolicy?view=graph-rest-1.0).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| version | Int32 | Version of the device configuration. Inherited from [deviceCompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicecompliancepolicy?view=graph-rest-1.0) |
| passwordRequired | Boolean | Require a password to unlock Windows device. |
| passwordBlockSimple | Boolean | Indicates whether or not to block simple password. |
| passwordExpirationDays | Int32 | Password expiration in days. |
| passwordMinimumLength | Int32 | The minimum password length. |
| passwordMinutesOfInactivityBeforeLock | Int32 | Minutes of inactivity before a password is required. |
| passwordMinimumCharacterSetCount | Int32 | The number of character sets required in the password. |
| passwordRequiredType | [requiredPasswordType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-requiredpasswordtype?view=graph-rest-1.0) | The required password type. The possible values are: `deviceDefault`, `alphanumeric`, `numeric`. |
| passwordPreviousPasswordBlockCount | Int32 | The number of previous passwords to prevent re-use of. Valid values 0 to 24 |
| osMinimumVersion | String | Minimum Windows 8.1 version. |
| osMaximumVersion | String | Maximum Windows 8.1 version. |
| storageRequireEncryption | Boolean | Indicates whether or not to require encryption on a windows 8.1 device. |

## Response

If successful, this method returns a `200 OK` response code and an updated [windows81CompliancePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windows81compliancepolicy?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/v1.0/deviceManagement/deviceCompliancePolicies/{deviceCompliancePolicyId}
Content-type: application/json
Content-length: 602

{
  "@odata.type": "#microsoft.graph.windows81CompliancePolicy",
  "description": "Description value",
  "displayName": "Display Name value",
  "version": 7,
  "passwordRequired": true,
  "passwordBlockSimple": true,
  "passwordExpirationDays": 6,
  "passwordMinimumLength": 5,
  "passwordMinutesOfInactivityBeforeLock": 5,
  "passwordMinimumCharacterSetCount": 0,
  "passwordRequiredType": "alphanumeric",
  "passwordPreviousPasswordBlockCount": 2,
  "osMinimumVersion": "Os Minimum Version value",
  "osMaximumVersion": "Os Maximum Version value",
  "storageRequireEncryption": true
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 774

{
  "@odata.type": "#microsoft.graph.windows81CompliancePolicy",
  "id": "6bb4b7e0-b7e0-6bb4-e0b7-b46be0b7b46b",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "description": "Description value",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "displayName": "Display Name value",
  "version": 7,
  "passwordRequired": true,
  "passwordBlockSimple": true,
  "passwordExpirationDays": 6,
  "passwordMinimumLength": 5,
  "passwordMinutesOfInactivityBeforeLock": 5,
  "passwordMinimumCharacterSetCount": 0,
  "passwordRequiredType": "alphanumeric",
  "passwordPreviousPasswordBlockCount": 2,
  "osMinimumVersion": "Os Minimum Version value",
  "osMaximumVersion": "Os Maximum Version value",
  "storageRequireEncryption": true
}
```
