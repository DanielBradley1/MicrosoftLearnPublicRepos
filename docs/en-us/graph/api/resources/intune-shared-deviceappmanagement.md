<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceappmanagement?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceAppManagement resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Singleton entity that acts as a container for all device app management functionality.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/intune-shared-deviceappmanagement-get?view=graph-rest-beta) | Read properties and relationships of the [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceappmanagement?view=graph-rest-beta) object. |  |
| [Update deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/intune-shared-deviceappmanagement-update?view=graph-rest-beta) | Update the properties of a [deviceAppManagement](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-deviceappmanagement?view=graph-rest-beta) object. |  |
| **Onboarding** |  |  |
| [syncMicrosoftStoreForBusinessApps action](https://learn.microsoft.com/en-us/graph/api/intune-shared-deviceappmanagement-syncmicrosoftstoreforbusinessapps?view=graph-rest-beta) | None | Syncs Intune account with Microsoft Store For Business |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| **Onboarding** |  |  |
| isEnabledForMicrosoftStoreForBusiness | Boolean | Whether the account is enabled for syncing applications from the Microsoft Store for Business. |
| microsoftStoreForBusinessLanguage | String | The locale information used to sync applications from the Microsoft Store for Business. Cultures that are specific to a country/region. The names of these cultures follow RFC 4646 \(Windows Vista and later\). The format is <languagecode2>-<country/regioncode2>, where <languagecode2> is a lowercase two-letter code derived from ISO 639-1 and <country/regioncode2> is an uppercase two-letter code derived from ISO 3166. For example, en-US for English \(United States\) is a specific culture. |
| microsoftStoreForBusinessLastCompletedApplicationSyncTime | DateTimeOffset | The last time an application sync from the Microsoft Store for Business was completed. |
| microsoftStoreForBusinessLastSuccessfulSyncDateTime | DateTimeOffset | The last time the apps from the Microsoft Store for Business were synced successfully for the account. |
| microsoftStoreForBusinessPortalSelection | [microsoftStoreForBusinessPortalSelectionOptions](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-microsoftstoreforbusinessportalselectionoptions?view=graph-rest-beta) | The end user portal information is used to sync applications from the Microsoft Store for Business to Intune Company Portal. There are three options to pick from \['Company portal only', 'Company portal and private store', 'Private store only'\]. The possible values are: `none`, `companyPortal`, `privateStore`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| **Apps** |  |  |
| enterpriseCodeSigningCertificates | [enterpriseCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-enterprisecodesigningcertificate?view=graph-rest-beta) collection | The Windows Enterprise Code Signing Certificate. |
| iosLobAppProvisioningConfigurations | [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration?view=graph-rest-beta) collection | The IOS Lob App Provisioning Configurations. |
| mobileAppCategories | [mobileAppCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-mobileappcategory?view=graph-rest-beta) collection | The mobile app categories. |
| mobileAppConfigurations | [managedDeviceMobileAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-manageddevicemobileappconfiguration?view=graph-rest-beta) collection | The Managed Device Mobile Application Configurations. |
| mobileApps | [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) collection | The mobile apps. |
| symantecCodeSigningCertificate | [symantecCodeSigningCertificate](https://learn.microsoft.com/en-us/graph/api/resources/intune-apps-symanteccodesigningcertificate?view=graph-rest-beta) | The WinPhone Symantec Code Signing Certificate. |
| **Books** |  |  |
| managedEBooks | [managedEBook](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebook?view=graph-rest-beta) collection | The Managed eBook. |
| managedEBookCategories | [managedEBookCategory](https://learn.microsoft.com/en-us/graph/api/resources/intune-books-managedebookcategory?view=graph-rest-beta) collection | The mobile eBook categories. |
| **Device management** |  |  |
| windowsManagementApp | [windowsManagementApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-windowsmanagementapp?view=graph-rest-beta) | Windows management app. |
| **Mobile app management \(MAM\)** |  |  |
| androidManagedAppProtections | [androidManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-androidmanagedappprotection?view=graph-rest-beta) collection | Android managed app policies. |
| defaultManagedAppProtections | [defaultManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-defaultmanagedappprotection?view=graph-rest-beta) collection | Default managed app policies. |
| iosManagedAppProtections | [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta) collection | iOS managed app policies. |
| managedAppPolicies | [managedAppPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedapppolicy?view=graph-rest-beta) collection | Managed app policies. |
| managedAppRegistrations | [managedAppRegistration](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappregistration?view=graph-rest-beta) collection | The managed app registrations. |
| managedAppStatuses | [managedAppStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappstatus?view=graph-rest-beta) collection | The managed app statuses. |
| mdmWindowsInformationProtectionPolicies | [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta) collection | Windows information protection for apps running on devices which are MDM enrolled. |
| targetedManagedAppConfigurations | [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta) collection | Targeted managed app configurations. |
| windowsInformationProtectionPolicies | [windowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionpolicy?view=graph-rest-beta) collection | Windows information protection for apps running on devices which are not MDM enrolled. |
| **Onboarding** |  |  |
| sideLoadingKeys | [sideLoadingKey](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-sideloadingkey?view=graph-rest-beta) collection | Side Loading Keys that are required for the Windows 8 and 8.1 Apps installation. |
| vppTokens | [vppToken](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-vpptoken?view=graph-rest-beta) collection | List of Vpp tokens for this organization. |
| **Policy Set** |  |  |
| policySets | [policySet](https://learn.microsoft.com/en-us/graph/api/resources/intune-policyset-policyset?view=graph-rest-beta) collection | The PolicySet of Policies and Applications |
| mobileApps | [mobileApp](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mobileapp?view=graph-rest-beta) collection | The mobile apps. |
| targetedManagedAppConfigurations | [targetedManagedAppConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-targetedmanagedappconfiguration?view=graph-rest-beta) collection | Targeted managed app configurations. |
| androidManagedAppProtections | [androidManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-androidmanagedappprotection?view=graph-rest-beta) collection | Android managed app policies. |
| iosManagedAppProtections | [iosManagedAppProtection](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-iosmanagedappprotection?view=graph-rest-beta) collection | iOS managed app policies. |
| mdmWindowsInformationProtectionPolicies | [mdmWindowsInformationProtectionPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-mdmwindowsinformationprotectionpolicy?view=graph-rest-beta) collection | Windows information protection for apps running on devices which are MDM enrolled. |
| iosLobAppProvisioningConfigurations | [iosLobAppProvisioningConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-ioslobappprovisioningconfiguration?view=graph-rest-beta) collection | The IOS Lob App Provisioning Configurations. |
| **Partner Integration** |  |  |
| deviceAppManagementTasks | [deviceAppManagementTask](https://learn.microsoft.com/en-us/graph/api/resources/intune-partnerintegration-deviceappmanagementtask?view=graph-rest-beta) collection | Device app management tasks. |
| **Unlock** |  |  |
| wdacSupplementalPolicies | [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-beta) collection | The collection of Windows Defender Application Control Supplemental Policies. |

## JSON Representation

Here is a JSON representation of the resource. Note that this is only an example; query responses to actual queries will contain the properties appropriate for the context.

```json
{
  "@odata.type": "#microsoft.graph.deviceAppManagement",
  "id": "String (identifier)",
  "microsoftStoreForBusinessLastSuccessfulSyncDateTime": "String (timestamp)",
  "isEnabledForMicrosoftStoreForBusiness": true,
  "microsoftStoreForBusinessLanguage": "String",
  "microsoftStoreForBusinessLastCompletedApplicationSyncTime": "String (timestamp)"
}
```
