<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_windows8applicationuserinfo-client-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_Windows8ApplicationUserInfo Client WMI Class

In Configuration Manager, the `SMS_Windows8ApplicationUserInfo` class is a client Windows Management Instrumentation \(WMI\) class that defines user information of an application.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_Windows8ApplicationUserInfo
{
      String FullName;
      String InstallState;
      String UserAccountName;
      String UserSecurityId;
};
```

## Methods

The `SMS_Windows8ApplicationUserInfo` class does not define any methods.

## Properties

`FullName` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

Full name of the user.

`InstallState` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

Installation state of the package. Possible values are:

| Value | Description |
| --- | --- |
| NotInstalled | The package has not been installed. |
| Staged | The package has been downloaded. |
| Installed | The package is ready for use. |

`UserAccountName` Data type: `String`

Access type: Read-only

Qualifiers: \[read\]

User account name.

`UserSecurityId` Data type: `String`

Access type: Read-only

Qualifiers: \[key, read\]

User security identifier.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).

## See Also

[Inventory Agent Client WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/inventory-agent-client-wmi-classes)
