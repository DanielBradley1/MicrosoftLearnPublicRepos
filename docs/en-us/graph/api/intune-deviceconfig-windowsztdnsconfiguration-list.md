<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsztdnsconfiguration-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-09 -->

# List windowsZtdnsConfigurations

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

List properties and relationships of the [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) objects.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | DeviceManagementConfiguration.Read.All, DeviceManagementConfiguration.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | DeviceManagementConfiguration.Read.All, DeviceManagementConfiguration.ReadWrite.All |

## HTTP Request

```http
GET /deviceManagement/deviceConfigurations
GET /deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.windowsDomainJoinConfiguration/networkAccessConfigurations
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

Do not supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) objects in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 2820

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.windowsZtdnsConfiguration",
      "id": "2d6a5581-5581-2d6a-8155-6a2d81556a2d",
      "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
      "roleScopeTagIds": [
        "Role Scope Tag Ids value"
      ],
      "supportsScopeTags": true,
      "deviceManagementApplicabilityRuleOsEdition": {
        "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsEdition",
        "osEditionTypes": [
          "windows10EnterpriseN"
        ],
        "name": "Name value",
        "ruleType": "exclude"
      },
      "deviceManagementApplicabilityRuleOsVersion": {
        "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleOsVersion",
        "minOSVersion": "Min OSVersion value",
        "maxOSVersion": "Max OSVersion value",
        "name": "Name value",
        "ruleType": "exclude"
      },
      "deviceManagementApplicabilityRuleDeviceMode": {
        "@odata.type": "microsoft.graph.deviceManagementApplicabilityRuleDeviceMode",
        "deviceMode": "sModeConfiguration",
        "name": "Name value",
        "ruleType": "exclude"
      },
      "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
      "description": "Description value",
      "displayName": "Display Name value",
      "version": 7,
      "auditModeEnabled": true,
      "exemptionRules": [
        {
          "@odata.type": "microsoft.graph.windowsZtdnsExemptionRule",
          "description": "Description value",
          "displayName": "Display Name value",
          "ipAddresses": [
            "Ip Addresses value"
          ]
        }
      ],
      "extendedKeyUsagesForClientAuthentication": [
        {
          "@odata.type": "microsoft.graph.extendedKeyUsage",
          "name": "Name value",
          "objectIdentifier": "Object Identifier value"
        }
      ],
      "hostsFileResolutionEnabled": true,
      "loopbackDnsForwarderEnabled": true,
      "loopbackTrafficBlocked": true,
      "maximumConnectionTimeInSeconds": 14,
      "secureDnsServers": [
        {
          "@odata.type": "microsoft.graph.windowsZtdnsSecureDnsServer",
          "displayName": "Display Name value",
          "dnsOverHttpsConfiguration": {
            "@odata.type": "microsoft.graph.windowsZtdnsSecureDnsServerDnsOverHttpsConfiguration",
            "httpsPort": 9,
            "queryUrl": "https://example.com/queryUrl/"
          },
          "dnsOverTlsConfiguration": {
            "@odata.type": "microsoft.graph.windowsZtdnsSecureDnsServerDnsOverTlsConfiguration",
            "certificateSubjectName": "Certificate Subject Name value",
            "tlsPort": 7
          },
          "ipAddress": "Ip Address value"
        }
      ]
    }
  ]
}
```
