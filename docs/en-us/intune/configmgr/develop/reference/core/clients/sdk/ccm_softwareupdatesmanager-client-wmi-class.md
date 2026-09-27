<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_softwareupdatesmanager-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_SoftwareUpdatesManager Client WMI Class

The `CCM_SoftwareUpdatesManager` WMI class is a client class, in Configuration Manager, that exposes methods to install, schedule and other actions on set of software updates.

This interface is equivalent to the ICCMUpdatesDeployment COM interface in the Configuration Manager 2007 SDK.

Important

The software update client side SDK will only return set of updates which are deployed to client from Configuration Manager site server, and are applicable, and are yet to be installed on the client.

The following syntax is simplified from the Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
class CCM_SoftwareUpdatesManager();
```

## Methods

The following table shows the methods in the `CCM_SoftwareUpdatesManager` class.

| Method | Description |
| --- | --- |
| [CancelDownload Method in Class CCM\_SoftwareUpdatesManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/canceldownload-method-in-class-ccm_softwareupdatesmanager) | Cancels an in-progress download of software updates during a deployment. |
| [GetAllUpdatesUserExperience Method in Class CCM\_SoftwareUpdatesManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager) | Gets the user experience mode that determines how software updates are displayed on a target computer. |
| [InstallUpdates Method in Class CCM\_SoftwareUpdatesManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/installupdates-method-in-class-ccm_softwareupdatesmanager) | Installs the software updates. |
| [PostponeUpdatesToNonBusinessHours Method in Class CCM\_SoftwareUpdatesManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/postponeupdatestononbusinesshours-method-in-class-ccm_softwareupdatesmanager) | Postpones a set of software updates to automatically install in non-business hours, which are specified by the user. |
| [SetAllUpdatesUserExperience Method in Class CCM\_SoftwareUpdatesManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/setallupdatesuserexperience-method-in-class-ccm_softwareupdatesmanager) | Sets the user experience mode that determines how software updates are displayed on a target computer. |

## Properties

The `CCM_SoftwareUpdatesManager` class does not define any properties.

## Remarks

This class is equivalent to the `ICCMUpdatesDeployment` class in Configuration Manager 2007 COM SDK.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
