<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-shared-devicemanagementderivedcredentialsettings-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# Update deviceManagementDerivedCredentialSettings

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) object.

```
    ## Permissions
```

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from most to least privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) |  |
| **Device configuration** | DeviceManagementConfiguration.ReadWrite.All |
| **Resource Access Policy** | DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application |  |
| **Device configuration** | DeviceManagementConfiguration.ReadWrite.All |
| **Resource Access Policy** | DeviceManagementConfiguration.ReadWrite.All |

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## HTTP Request

```http
PATCH /deviceManagement/derivedCredentials/{deviceManagementDerivedCredentialSettingsId}
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/derivedCredentialSettings
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.iosVpnConfiguration/derivedCredentialSettings
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.iosEnterpriseWiFiConfiguration/derivedCredentialSettings
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.iosEasEmailProfileConfiguration/derivedCredentialSettings
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.iosDerivedCredentialAuthenticationConfiguration/derivedCredentialSettings
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the Derived Credential |
| **RA Policy** |  |  |
| helpUrl | String | The URL that will be accessible to end users as they retrieve a derived credential using the Company Portal. |
| displayName | String | The display name for the profile. |
| issuer | [deviceManagementDerivedCredentialIssuer](https://learn.microsoft.com/en-us/graph/resources/intune-shared-devicemanagementderivedcredentialissuer.md?view=graph-rest-beta) | The derived credential provider to use. The possible values are: `intercede`, `entrustDatacard`, `purebred`. |
| notificationType | [deviceManagementDerivedCredentialNotificationType](https://learn.microsoft.com/en-us/graph/resources/intune-shared-devicemanagementderivedcredentialnotificationtype.md?view=graph-rest-beta) | The methods used to inform the end user to open Company Portal to deliver Wi-Fi, VPN, or email profiles that use certificates to the device. The possible values are: `none`, `companyPortal`, `email`. |

## Response

If successful, this method returns a `200 OK` response code and an updated [deviceManagementDerivedCredentialSettings](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-devicemanagementderivedcredentialsettings?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations/{deviceConfigurationId}/derivedCredentialSettings
Content-type: application/json
Content-length: 83

{
  "@odata.type": "#microsoft.graph.deviceManagementDerivedCredentialSettings"
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 132

{
  "@odata.type": "#microsoft.graph.deviceManagementDerivedCredentialSettings",
  "id": "bc650741-0741-bc65-4107-65bc410765bc"
}
```
