<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# mdmWindowsInformationProtectionPolicy resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Policy for Windows information protection with MDM

Inherits from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mdmWindowsInformationProtectionPolicies](https://learn.microsoft.com/en-us/graph/api/intune-shared-mdmwindowsinformationprotectionpolicy-list?view=graph-rest-beta) | [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta) collection | List properties and relationships of the [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta) objects. |
| [Get mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/intune-shared-mdmwindowsinformationprotectionpolicy-get?view=graph-rest-beta) | [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta) | Read properties and relationships of the [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta) object. |
| [Create mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/intune-shared-mdmwindowsinformationprotectionpolicy-create?view=graph-rest-beta) | [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta) | Create a new [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta) object. |
| [Delete mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/intune-shared-mdmwindowsinformationprotectionpolicy-delete?view=graph-rest-beta) | None | Deletes a [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta). |
| [Update mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/intune-shared-mdmwindowsinformationprotectionpolicy-update?view=graph-rest-beta) | [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta) | Update the properties of a [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta) object. |
| **Policy Set** |  |  |
| [hasPayloadLinks action](https://learn.microsoft.com/en-us/graph/api/intune-shared-mdmwindowsinformationprotectionpolicy-haspayloadlinks?view=graph-rest-beta) | [hasPayloadLinkResultItem](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-haspayloadlinkresultitem?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| displayName | String | Policy display name. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| description | String | The policy's description. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| createdDateTime | DateTimeOffset | The date and time the policy was created. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | Last time the policy was modified. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| roleScopeTagIds | String collection | List of Scope Tags for this Entity instance. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| version | String | Version of the entity. Inherited from [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) |
| enforcementLevel | [windowsInformationProtectionEnforcementLevel](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionenforcementlevel?view=graph-rest-beta) | WIP enforcement level.See the Enum definition for supported values Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta). The possible values are: `noProtection`, `encryptAndAuditOnly`, `encryptAuditAndPrompt`, `encryptAuditAndBlock`. |
| enterpriseDomain | String | Primary enterprise domain Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| enterpriseProtectedDomainNames | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-beta) collection | List of enterprise domains to be protected Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| protectionUnderLockConfigRequired | Boolean | Specifies whether the protection under lock feature \(also known as encrypt under pin\) should be configured Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| dataRecoveryCertificate | [windowsInformationProtectionDataRecoveryCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondatarecoverycertificate?view=graph-rest-beta) | Specifies a recovery certificate that can be used for data recovery of encrypted files. This is the same as the data recovery agent\(DRA\) certificate for encrypting file system\(EFS\) Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| revokeOnUnenrollDisabled | Boolean | This policy controls whether to revoke the WIP keys when a device unenrolls from the management service. If set to 1 \(Don't revoke keys\), the keys will not be revoked and the user will continue to have access to protected files after unenrollment. If the keys are not revoked, there will be no revoked file cleanup subsequently. Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| rightsManagementServicesTemplateId | Guid | TemplateID GUID to use for RMS encryption. The RMS template allows the IT admin to configure the details about who has access to RMS-protected file and how long they have access Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| azureRightsManagementServicesAllowed | Boolean | Specifies whether to allow Azure RMS encryption for WIP Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| iconsVisible | Boolean | Determines whether overlays are added to icons for WIP protected files in Explorer and enterprise only app tiles in the Start menu. Starting in Windows 10, version 1703 this setting also configures the visibility of the WIP icon in the title bar of a WIP-protected app Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| protectedApps | [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-beta) collection | Protected applications can access enterprise data and the data handled by those applications are protected with encryption Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| exemptApps | [windowsInformationProtectionApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapp?view=graph-rest-beta) collection | Exempt applications can also access enterprise data, but the data handled by those applications are not protected. This is because some critical enterprise applications may have compatibility problems with encrypted data. Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| enterpriseNetworkDomainNames | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-beta) collection | This is the list of domains that comprise the boundaries of the enterprise. Data from one of these domains that is sent to a device will be considered enterprise data and protected These locations will be considered a safe destination for enterprise data to be shared to Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| enterpriseProxiedDomains | [windowsInformationProtectionProxiedDomainCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionproxieddomaincollection?view=graph-rest-beta) collection | Contains a list of Enterprise resource domains hosted in the cloud that need to be protected. Connections to these resources are considered enterprise data. If a proxy is paired with a cloud resource, traffic to the cloud resource will be routed through the enterprise network via the denoted proxy server \(on Port 80\). A proxy server used for this purpose must also be configured using the EnterpriseInternalProxyServers policy Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| enterpriseIPRanges | [windowsInformationProtectionIPRangeCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectioniprangecollection?view=graph-rest-beta) collection | Sets the enterprise IP ranges that define the computers in the enterprise network. Data that comes from those computers will be considered part of the enterprise and protected. These locations will be considered a safe destination for enterprise data to be shared to Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| enterpriseIPRangesAreAuthoritative | Boolean | Boolean value that tells the client to accept the configured list and not to use heuristics to attempt to find other subnets. Default is false Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| enterpriseProxyServers | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-beta) collection | This is a list of proxy servers. Any server not on this list is considered non-enterprise Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| enterpriseInternalProxyServers | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-beta) collection | This is the comma-separated list of internal proxy servers. For example, "157.54.14.28, 157.54.11.118, 10.202.14.167, 157.53.14.163, 157.69.210.59". These proxies have been configured by the admin to connect to specific resources on the Internet. They are considered to be enterprise network locations. The proxies are only leveraged in configuring the EnterpriseProxiedDomains policy to force traffic to the matched domains through these proxies Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| enterpriseProxyServersAreAuthoritative | Boolean | Boolean value that tells the client to accept the configured list of proxies and not try to detect other work proxies. Default is false Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| neutralDomainResources | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-beta) collection | List of domain names that can used for work or personal resource Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| indexingEncryptedStoresOrItemsBlocked | Boolean | This switch is for the Windows Search Indexer, to allow or disallow indexing of items Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| smbAutoEncryptedFileExtensions | [windowsInformationProtectionResourceCollection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionresourcecollection?view=graph-rest-beta) collection | Specifies a list of file extensions, so that files with these extensions are encrypted when copying from an SMB share within the corporate boundary Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| isAssigned | Boolean | Indicates if the policy is deployed to any inclusion groups or not. Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| **Mobile app management \(MAM\)** |  |  |
| protectedAppLockerFiles | [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-beta) collection | Another way to input protected apps through xml files Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| exemptAppLockerFiles | [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-beta) collection | Another way to input exempt apps through xml files Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |
| assignments | [targetedManagedAppPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-targetedmanagedapppolicyassignment?view=graph-rest-beta) collection | Navigation property to list of security groups targeted for policy. Inherited from [windowsInformationProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotection?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mdmWindowsInformationProtectionPolicy",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
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
          "@odata.type": "microsoft.graph.iPv6Range",
          "lowerAddress": "String",
          "upperAddress": "String"
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
