<!-- Source: https://learn.microsoft.com/en-us/graph/api/intune-mam-mdmwindowsinformationprotectionpolicy-create?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# Create mdmWindowsInformationProtectionPolicy

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Create a new [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-mdmwindowsinformationprotectionpolicy?view=graph-rest-1.0) object.

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
POST /deviceAppManagement/mdmWindowsInformationProtectionPolicies
```

## Request headers

| Header | Value |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Accept | application/json |

## Request body

In the request body, supply a JSON representation for the mdmWindowsInformationProtectionPolicy object.

The following table shows the properties that are required when you create the mdmWindowsInformationProtectionPolicy.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Policy display name. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| description | String | The policy's description. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | The date and time the policy was created. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | Last time the policy was modified. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| id | String | Key of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| version | String | Version of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| enforcementLevel | [windowsInformationProtectionEnforcementLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionenforcementlevel?view=graph-rest-1.0) | WIP enforcement level.See the Enum definition for supported values Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0). The possible values are: `noProtection`, `encryptAndAuditOnly`, `encryptAuditAndPrompt`, `encryptAuditAndBlock`. |
| enterpriseDomain | String | Primary enterprise domain Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| enterpriseProtectedDomainNames | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | List of enterprise domains to be protected Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| protectionUnderLockConfigRequired | Boolean | Specifies whether the protection under lock feature \(also known as encrypt under pin\) should be configured Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| dataRecoveryCertificate | [windowsInformationProtectionDataRecoveryCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondatarecoverycertificate?view=graph-rest-1.0) | Specifies a recovery certificate that can be used for data recovery of encrypted files. This is the same as the data recovery agent\(DRA\) certificate for encrypting file system\(EFS\) Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| revokeOnUnenrollDisabled | Boolean | This policy controls whether to revoke the WIP keys when a device unenrolls from the management service. If set to 1 \(Don't revoke keys\), the keys will not be revoked and the user will continue to have access to protected files after unenrollment. If the keys are not revoked, there will be no revoked file cleanup subsequently. Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| rightsManagementServicesTemplateId | Guid | TemplateID GUID to use for RMS encryption. The RMS template allows the IT admin to configure the details about who has access to RMS-protected file and how long they have access Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| azureRightsManagementServicesAllowed | Boolean | Specifies whether to allow Azure RMS encryption for WIP Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| iconsVisible | Boolean | Determines whether overlays are added to icons for WIP protected files in Explorer and enterprise only app tiles in the Start menu. Starting in Windows 10, version 1703 this setting also configures the visibility of the WIP icon in the title bar of a WIP-protected app Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| protectedApps | [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-1.0) collection | Protected applications can access enterprise data and the data handled by those applications are protected with encryption Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| exemptApps | [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-1.0) collection | Exempt applications can also access enterprise data, but the data handled by those applications are not protected. This is because some critical enterprise applications may have compatibility problems with encrypted data. Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| enterpriseNetworkDomainNames | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | This is the list of domains that comprise the boundaries of the enterprise. Data from one of these domains that is sent to a device will be considered enterprise data and protected These locations will be considered a safe destination for enterprise data to be shared to Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| enterpriseProxiedDomains | [windowsInformationProtectionProxiedDomainCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionproxieddomaincollection?view=graph-rest-1.0) collection | Contains a list of Enterprise resource domains hosted in the cloud that need to be protected. Connections to these resources are considered enterprise data. If a proxy is paired with a cloud resource, traffic to the cloud resource will be routed through the enterprise network via the denoted proxy server \(on Port 80\). A proxy server used for this purpose must also be configured using the EnterpriseInternalProxyServers policy Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| enterpriseIPRanges | [windowsInformationProtectionIPRangeCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectioniprangecollection?view=graph-rest-1.0) collection | Sets the enterprise IP ranges that define the computers in the enterprise network. Data that comes from those computers will be considered part of the enterprise and protected. These locations will be considered a safe destination for enterprise data to be shared to Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| enterpriseIPRangesAreAuthoritative | Boolean | Boolean value that tells the client to accept the configured list and not to use heuristics to attempt to find other subnets. Default is false Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| enterpriseProxyServers | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | This is a list of proxy servers. Any server not on this list is considered non-enterprise Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| enterpriseInternalProxyServers | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | This is the comma-separated list of internal proxy servers. For example, "157.54.14.28, 157.54.11.118, 10.202.14.167, 157.53.14.163, 157.69.210.59". These proxies have been configured by the admin to connect to specific resources on the Internet. They are considered to be enterprise network locations. The proxies are only leveraged in configuring the EnterpriseProxiedDomains policy to force traffic to the matched domains through these proxies Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| enterpriseProxyServersAreAuthoritative | Boolean | Boolean value that tells the client to accept the configured list of proxies and not try to detect other work proxies. Default is false Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| neutralDomainResources | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | List of domain names that can used for work or personal resource Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| indexingEncryptedStoresOrItemsBlocked | Boolean | This switch is for the Windows Search Indexer, to allow or disallow indexing of items Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| smbAutoEncryptedFileExtensions | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | Specifies a list of file extensions, so that files with these extensions are encrypted when copying from an SMB share within the corporate boundary Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |
| isAssigned | Boolean | Indicates if the policy is deployed to any inclusion groups or not. Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) |

## Response

If successful, this method returns a `201 Created` response code and a [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-mdmwindowsinformationprotectionpolicy?view=graph-rest-1.0) object in the response body.

## Example

### Request

Here is an example of the request.

```http
POST https://graph.microsoft.com/v1.0/deviceAppManagement/mdmWindowsInformationProtectionPolicies
Content-type: application/json
Content-length: 3905

{
  "@odata.type": "#microsoft.graph.mdmWindowsInformationProtectionPolicy",
  "displayName": "Display Name value",
  "description": "Description value",
  "version": "Version value",
  "enforcementLevel": "encryptAndAuditOnly",
  "enterpriseDomain": "Enterprise Domain value",
  "enterpriseProtectedDomainNames": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "protectionUnderLockConfigRequired": true,
  "dataRecoveryCertificate": {
    "@odata.type": "microsoft.graph.windowsInformationProtectionDataRecoveryCertificate",
    "subjectName": "Subject Name value",
    "description": "Description value",
    "expirationDateTime": "2016-12-31T23:57:57.2481234-08:00",
    "certificate": "Y2VydGlmaWNhdGU="
  },
  "revokeOnUnenrollDisabled": true,
  "rightsManagementServicesTemplateId": "abf7b16f-b16f-abf7-6fb1-f7ab6fb1f7ab",
  "azureRightsManagementServicesAllowed": true,
  "iconsVisible": true,
  "protectedApps": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionStoreApp",
      "displayName": "Display Name value",
      "description": "Description value",
      "publisherName": "Publisher Name value",
      "productName": "Product Name value",
      "denied": true
    }
  ],
  "exemptApps": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionStoreApp",
      "displayName": "Display Name value",
      "description": "Description value",
      "publisherName": "Publisher Name value",
      "productName": "Product Name value",
      "denied": true
    }
  ],
  "enterpriseNetworkDomainNames": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "enterpriseProxiedDomains": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionProxiedDomainCollection",
      "displayName": "Display Name value",
      "proxiedDomains": [
        {
          "@odata.type": "microsoft.graph.proxiedDomain",
          "ipAddressOrFQDN": "Ip Address Or FQDN value",
          "proxy": "Proxy value"
        }
      ]
    }
  ],
  "enterpriseIPRanges": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionIPRangeCollection",
      "displayName": "Display Name value",
      "ranges": [
        {
          "@odata.type": "microsoft.graph.iPv6Range",
          "lowerAddress": "Lower Address value",
          "upperAddress": "Upper Address value"
        }
      ]
    }
  ],
  "enterpriseIPRangesAreAuthoritative": true,
  "enterpriseProxyServers": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "enterpriseInternalProxyServers": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "enterpriseProxyServersAreAuthoritative": true,
  "neutralDomainResources": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "indexingEncryptedStoresOrItemsBlocked": true,
  "smbAutoEncryptedFileExtensions": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "isAssigned": true
}
```

### Response

Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 4077

{
  "@odata.type": "#microsoft.graph.mdmWindowsInformationProtectionPolicy",
  "displayName": "Display Name value",
  "description": "Description value",
  "createdDateTime": "2017-01-01T00:02:43.5775965-08:00",
  "lastModifiedDateTime": "2017-01-01T00:00:35.1329464-08:00",
  "id": "8efb0c35-0c35-8efb-350c-fb8e350cfb8e",
  "version": "Version value",
  "enforcementLevel": "encryptAndAuditOnly",
  "enterpriseDomain": "Enterprise Domain value",
  "enterpriseProtectedDomainNames": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "protectionUnderLockConfigRequired": true,
  "dataRecoveryCertificate": {
    "@odata.type": "microsoft.graph.windowsInformationProtectionDataRecoveryCertificate",
    "subjectName": "Subject Name value",
    "description": "Description value",
    "expirationDateTime": "2016-12-31T23:57:57.2481234-08:00",
    "certificate": "Y2VydGlmaWNhdGU="
  },
  "revokeOnUnenrollDisabled": true,
  "rightsManagementServicesTemplateId": "abf7b16f-b16f-abf7-6fb1-f7ab6fb1f7ab",
  "azureRightsManagementServicesAllowed": true,
  "iconsVisible": true,
  "protectedApps": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionStoreApp",
      "displayName": "Display Name value",
      "description": "Description value",
      "publisherName": "Publisher Name value",
      "productName": "Product Name value",
      "denied": true
    }
  ],
  "exemptApps": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionStoreApp",
      "displayName": "Display Name value",
      "description": "Description value",
      "publisherName": "Publisher Name value",
      "productName": "Product Name value",
      "denied": true
    }
  ],
  "enterpriseNetworkDomainNames": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "enterpriseProxiedDomains": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionProxiedDomainCollection",
      "displayName": "Display Name value",
      "proxiedDomains": [
        {
          "@odata.type": "microsoft.graph.proxiedDomain",
          "ipAddressOrFQDN": "Ip Address Or FQDN value",
          "proxy": "Proxy value"
        }
      ]
    }
  ],
  "enterpriseIPRanges": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionIPRangeCollection",
      "displayName": "Display Name value",
      "ranges": [
        {
          "@odata.type": "microsoft.graph.iPv6Range",
          "lowerAddress": "Lower Address value",
          "upperAddress": "Upper Address value"
        }
      ]
    }
  ],
  "enterpriseIPRangesAreAuthoritative": true,
  "enterpriseProxyServers": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "enterpriseInternalProxyServers": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "enterpriseProxyServersAreAuthoritative": true,
  "neutralDomainResources": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "indexingEncryptedStoresOrItemsBlocked": true,
  "smbAutoEncryptedFileExtensions": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "Display Name value",
      "resources": [
        "Resources value"
      ]
    }
  ],
  "isAssigned": true
}
```
