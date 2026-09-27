<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/ccm_servicewindowmanager-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_ServiceWindowManager Client WMI Class

The `CCM_ServiceWindowManager` WMI class is a client class, in Configuration Manager, manages service windows on the client computer.

The following syntax is simplified from the Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
class CCM_ServiceWindowManager();
```

## Methods

The following table shows the methods in the `CCM_ServiceWindowManager` class.

| Method | Description |
| --- | --- |
| [GetCurrentWindowAvailableTime Method in Class CCM\_SoftwareUpdatesManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getcurrentwindowavailabletime-method-in-class-ccm_servicewindowmanager) | Gets the time remaining in a currently-active service window for a specified type. |
| [GetNextServiceWindowID Method in Class CCM\_SoftwareUpdatesManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/getnextservicewindowid-method-in-class-ccm_servicewindowmanager) | Gets the identifier of the next service window closest to the current time. |
| [IsFutureWindowAvailable Method in Class CCM\_SoftwareUpdatesManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/isfuturewindowavailable-method-in-class-ccm_servicewindowmanager) | Determines whether a service window of a specified type and a given duration is going to be available. |
| [IsWindowAvailableNow Method in Class CCM\_SoftwareUpdatesManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/iswindowavailablenow-method-in-class-ccm_servicewindowmanager) | Determines whether a service window of a specified type and a given duration is available to run at the point of time when the call is made. |

## Properties

The `CCM_ServiceWindowManager` class does not define any properties.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
