<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/cleardeploymentlocksforcollection-method-in-class-sms_collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ClearDeploymentLocksForCollection Method in Class SMS\_Collection

The `ClearDeploymentLocksForCollection` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, clears deployment locks for a selected collection. For example, if the server group option is selected for a collection, and an administrator sees that the deployments to the collection are stuck, then the administrator can use this method to release the deployment lock from a non-responsive client, allowing the other members of the collection to acquire a deployment lock.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ClearDeploymentLocksForCollection();
```

#### Parameters

None.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) [SMS\_Site Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class)
