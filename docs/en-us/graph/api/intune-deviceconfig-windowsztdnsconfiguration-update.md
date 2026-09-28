<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-windowsztdnsconfiguration-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-09 -->

# Update windowsZtdnsConfiguration

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Update the properties of a [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) object.

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
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/groupAssignments/{deviceConfigurationGroupAssignmentId}/deviceConfiguration
PATCH /deviceManagement/deviceConfigurations/{deviceConfigurationId}/microsoft.graph.windowsDomainJoinConfiguration/networkAccessConfigurations/{deviceConfigurationId}
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) object.

The following table shows the properties that are required when you create the [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta).

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime the object was last modified. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| supportsScopeTags | Boolean | Indicates whether or not the underlying Device Configuration supports the assignment of scope tags. Assigning to the ScopeTags property is not allowed when this value is false and entities will not be visible to scoped users. This occurs for Legacy policies created in Silverlight and can be resolved by deleting and recreating the policy in the Azure Portal. This property is read-only. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleOsEdition | [deviceManagementApplicabilityRuleOsEdition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruleosedition?view=graph-rest-beta) | The OS edition applicability for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleOsVersion | [deviceManagementApplicabilityRuleOsVersion](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruleosversion?view=graph-rest-beta) | The OS version applicability rule for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| deviceManagementApplicabilityRuleDeviceMode | [deviceManagementApplicabilityRuleDeviceMode](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-devicemanagementapplicabilityruledevicemode?view=graph-rest-beta) | The device mode applicability rule for this Policy. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | DateTime the object was created. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| description | String | Admin provided description of the Device Configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| displayName | String | Admin provided name of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| version | Int32 | Version of the device configuration. Inherited from [deviceConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceconfiguration?view=graph-rest-beta) |
| auditModeEnabled | Boolean | Indicates the audit operational mode. When true, unsecured traffic will be logged but not blocked. When false, unsecured DNS traffic will be blocked unless specifically exempted. |
| exemptionRules | [windowsZtdnsExemptionRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsexemptionrule?view=graph-rest-beta) collection | Exemptions to the ZTDNS rules, allowing access to specific addresses or subnets via unsecured lookup. This collection can contain a maximum of 500 elements. |
| extendedKeyUsagesForClientAuthentication | [extendedKeyUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-extendedkeyusage?view=graph-rest-beta) collection | Extended key usage definitions for client authentication with secure DNS servers. This collection can contain a maximum of 500 elements. |
| hostsFileResolutionEnabled | Boolean | Indicates whether the DNS Client can resolve queries using the hosts file. |
| loopbackDnsForwarderEnabled | Boolean | Creates a localhost DNS server for securely forwarding plaintext queries to trusted DNS servers. |
| loopbackTrafficBlocked | Boolean | Indicates whether traffic to loopback addresses should be blocked. |
| maximumConnectionTimeInSeconds | Int32 | Maximum time in seconds for which connections to an IP address will be allowed after successful name resolution. Valid values 30 to 604800 |
| secureDnsServers | [windowsZtdnsSecureDnsServer](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnssecurednsserver?view=graph-rest-beta) collection | Collection of secure DNS servers used to resolve ZTDNS queries. Must contain at least one item. This collection can contain a maximum of 500 elements. |

## Response

If successful, this method returns a `200 OK` response code and an updated [windowsZtdnsConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-windowsztdnsconfiguration?view=graph-rest-beta) object in the response body.

## Example

### Request

Here is an example of the request.

```http
PATCH https://graph.microsoft.com/beta/deviceManagement/deviceConfigurations/{deviceConfigurationId}
Content-type: application/json
Content-length: 2331

{
  "@odata.type": "#microsoft.graph.windowsZtdnsConfiguration",
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
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 2503

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
```
