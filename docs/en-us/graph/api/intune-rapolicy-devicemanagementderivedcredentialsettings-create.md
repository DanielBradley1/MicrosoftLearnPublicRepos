<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-devicemanagementderivedcredentialsettings-create?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Create deviceManagementDerivedCredentialSettings

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) object.

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
POST /deviceManagement/derivedCredentials
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the deviceManagementDerivedCredentialSettings object.

The following table shows the properties that are required when you create the deviceManagementDerivedCredentialSettings.

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the Derived Credential |
| helpUrl | String | The URL that will be accessible to end users as they retrieve a derived credential using the Company Portal. |
| displayName | String | The display name for the profile. |
| issuer | [deviceManagementDerivedCredentialIssuer](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementderivedcredentialissuer?view=graph-rest-beta) | The derived credential provider to use. Possible values are: `intercede`, `entrustDatacard`, `purebred`, `xTec`. |
| notificationType | [deviceManagementDerivedCredentialNotificationType](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementderivedcredentialnotificationtype?view=graph-rest-beta) | The methods used to inform the end user to open Company Portal to deliver Wi-Fi, VPN, or email profiles that use certificates to the device. Possible values are: `none`, `companyPortal`, `email`. |
| renewalThresholdPercentage | Int32 | The nominal percentage of time before certificate renewal is initiated by the client. |

## Response

If successful, this method returns a `201 Created` response code and a [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/deviceManagement/derivedCredentials
Content-type: application/json
Content-length: 278

{
  "@odata.type": "#microsoft.graph.deviceManagementDerivedCredentialSettings",
  "helpUrl": "https://example.com/helpUrl/",
  "displayName": "Display Name value",
  "issuer": "entrustDatacard",
  "notificationType": "companyPortal",
  "renewalThresholdPercentage": 10
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 327

{
  "@odata.type": "#microsoft.graph.deviceManagementDerivedCredentialSettings",
  "id": "bc650741-0741-bc65-4107-65bc410765bc",
  "helpUrl": "https://example.com/helpUrl/",
  "displayName": "Display Name value",
  "issuer": "entrustDatacard",
  "notificationType": "companyPortal",
  "renewalThresholdPercentage": 10
}
```
