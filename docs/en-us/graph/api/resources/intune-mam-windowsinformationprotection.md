<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-13 -->

# windowsInformationProtection resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Policy for Windows information protection to configure detailed management settings

Inherits from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsInformationProtections](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotection-list?view=graph-rest-1.0) | [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) collection | List properties and relationships of the [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) objects. |
| [Get windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotection-get?view=graph-rest-1.0) | [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) | Read properties and relationships of the [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-1.0) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotection-assign?view=graph-rest-1.0) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Policy display name. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| description | String | The policy's description. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| createdDateTime | DateTimeOffset | The date and time the policy was created. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| lastModifiedDateTime | DateTimeOffset | Last time the policy was modified. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| id | String | Key of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| version | String | Version of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-1.0) |
| enforcementLevel | [windowsInformationProtectionEnforcementLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionenforcementlevel?view=graph-rest-1.0) | WIP enforcement level.See the Enum definition for supported values. The possible values are: `noProtection`, `encryptAndAuditOnly`, `encryptAuditAndPrompt`, `encryptAuditAndBlock`. |
| enterpriseDomain | String | Primary enterprise domain |
| enterpriseProtectedDomainNames | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | List of enterprise domains to be protected |
| protectionUnderLockConfigRequired | Boolean | Specifies whether the protection under lock feature \(also known as encrypt under pin\) should be configured |
| dataRecoveryCertificate | [windowsInformationProtectionDataRecoveryCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondatarecoverycertificate?view=graph-rest-1.0) | Specifies a recovery certificate that can be used for data recovery of encrypted files. This is the same as the data recovery agent\(DRA\) certificate for encrypting file system\(EFS\) |
| revokeOnUnenrollDisabled | Boolean | This policy controls whether to revoke the WIP keys when a device unenrolls from the management service. If set to 1 \(Don't revoke keys\), the keys will not be revoked and the user will continue to have access to protected files after unenrollment. If the keys are not revoked, there will be no revoked file cleanup subsequently. |
| rightsManagementServicesTemplateId | Guid | TemplateID GUID to use for RMS encryption. The RMS template allows the IT admin to configure the details about who has access to RMS-protected file and how long they have access |
| azureRightsManagementServicesAllowed | Boolean | Specifies whether to allow Azure RMS encryption for WIP |
| iconsVisible | Boolean | Determines whether overlays are added to icons for WIP protected files in Explorer and enterprise only app tiles in the Start menu. Starting in Windows 10, version 1703 this setting also configures the visibility of the WIP icon in the title bar of a WIP-protected app |
| protectedApps | [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-1.0) collection | Protected applications can access enterprise data and the data handled by those applications are protected with encryption |
| exemptApps | [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-1.0) collection | Exempt applications can also access enterprise data, but the data handled by those applications are not protected. This is because some critical enterprise applications may have compatibility problems with encrypted data. |
| enterpriseNetworkDomainNames | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | This is the list of domains that comprise the boundaries of the enterprise. Data from one of these domains that is sent to a device will be considered enterprise data and protected These locations will be considered a safe destination for enterprise data to be shared to |
| enterpriseProxiedDomains | [windowsInformationProtectionProxiedDomainCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionproxieddomaincollection?view=graph-rest-1.0) collection | Contains a list of Enterprise resource domains hosted in the cloud that need to be protected. Connections to these resources are considered enterprise data. If a proxy is paired with a cloud resource, traffic to the cloud resource will be routed through the enterprise network via the denoted proxy server \(on Port 80\). A proxy server used for this purpose must also be configured using the EnterpriseInternalProxyServers policy |
| enterpriseIPRanges | [windowsInformationProtectionIPRangeCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectioniprangecollection?view=graph-rest-1.0) collection | Sets the enterprise IP ranges that define the computers in the enterprise network. Data that comes from those computers will be considered part of the enterprise and protected. These locations will be considered a safe destination for enterprise data to be shared to |
| enterpriseIPRangesAreAuthoritative | Boolean | Boolean value that tells the client to accept the configured list and not to use heuristics to attempt to find other subnets. Default is false |
| enterpriseProxyServers | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | This is a list of proxy servers. Any server not on this list is considered non-enterprise |
| enterpriseInternalProxyServers | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | This is the comma-separated list of internal proxy servers. For example, "157.54.14.28, 157.54.11.118, 10.202.14.167, 157.53.14.163, 157.69.210.59". These proxies have been configured by the admin to connect to specific resources on the Internet. They are considered to be enterprise network locations. The proxies are only leveraged in configuring the EnterpriseProxiedDomains policy to force traffic to the matched domains through these proxies |
| enterpriseProxyServersAreAuthoritative | Boolean | Boolean value that tells the client to accept the configured list of proxies and not try to detect other work proxies. Default is false |
| neutralDomainResources | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | List of domain names that can used for work or personal resource |
| indexingEncryptedStoresOrItemsBlocked | Boolean | This switch is for the Windows Search Indexer, to allow or disallow indexing of items |
| smbAutoEncryptedFileExtensions | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-1.0) collection | Specifies a list of file extensions, so that files with these extensions are encrypted when copying from an SMB share within the corporate boundary |
| isAssigned | Boolean | Indicates if the policy is deployed to any inclusion groups or not. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| protectedAppLockerFiles | [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0) collection | Another way to input protected apps through xml files |
| exemptAppLockerFiles | [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0) collection | Another way to input exempt apps through xml files |
| assignments | [targetedManagedAppPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedapppolicyassignment?view=graph-rest-1.0) collection | Navigation property to list of security groups targeted for policy. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsInformationProtection",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "id": "String (identifier)",
  "version": "String",
  "enforcementLevel": "String",
  "enterpriseDomain": "String",
  "enterpriseProtectedDomainNames": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "String",
      "resources": [
        "String"
      ]
    }
  ],
  "protectionUnderLockConfigRequired": true,
  "dataRecoveryCertificate": {
    "@odata.type": "microsoft.graph.windowsInformationProtectionDataRecoveryCertificate",
    "subjectName": "String",
    "description": "String",
    "expirationDateTime": "String (timestamp)",
    "certificate": "binary"
  },
  "revokeOnUnenrollDisabled": true,
  "rightsManagementServicesTemplateId": "Guid",
  "azureRightsManagementServicesAllowed": true,
  "iconsVisible": true,
  "protectedApps": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionStoreApp",
      "displayName": "String",
      "description": "String",
      "publisherName": "String",
      "productName": "String",
      "denied": true
    }
  ],
  "exemptApps": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionStoreApp",
      "displayName": "String",
      "description": "String",
      "publisherName": "String",
      "productName": "String",
      "denied": true
    }
  ],
  "enterpriseNetworkDomainNames": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "String",
      "resources": [
        "String"
      ]
    }
  ],
  "enterpriseProxiedDomains": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionProxiedDomainCollection",
      "displayName": "String",
      "proxiedDomains": [
        {
          "@odata.type": "microsoft.graph.proxiedDomain",
          "ipAddressOrFQDN": "String",
          "proxy": "String"
        }
      ]
    }
  ],
  "enterpriseIPRanges": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionIPRangeCollection",
      "displayName": "String",
      "ranges": [
        {
          "@odata.type": "microsoft.graph.ipRange"
        }
      ]
    }
  ],
  "enterpriseIPRangesAreAuthoritative": true,
  "enterpriseProxyServers": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "String",
      "resources": [
        "String"
      ]
    }
  ],
  "enterpriseInternalProxyServers": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "String",
      "resources": [
        "String"
      ]
    }
  ],
  "enterpriseProxyServersAreAuthoritative": true,
  "neutralDomainResources": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "String",
      "resources": [
        "String"
      ]
    }
  ],
  "indexingEncryptedStoresOrItemsBlocked": true,
  "smbAutoEncryptedFileExtensions": [
    {
      "@odata.type": "microsoft.graph.windowsInformationProtectionResourceCollection",
      "displayName": "String",
      "resources": [
        "String"
      ]
    }
  ],
  "isAssigned": true
}
```
