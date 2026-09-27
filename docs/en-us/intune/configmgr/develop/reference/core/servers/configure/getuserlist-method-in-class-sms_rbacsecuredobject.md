<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getuserlist-method-in-class-sms_rbacsecuredobject -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetUserList Method in Class SMS\_RbacSecuredObject

The `GetUserList` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, returns the list of users who have been granted permission to this object.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
UInt32 GetUserList(
     SMS_BaseClass ref ObjectPath,
     String UserNames[],
     Uint32 PermittedOperations[]
);
```

#### Parameters

`ObjectPath` Data type: `SMS_BaseClass`

Qualifiers: \[in\]

The path of the object.

`UserNames` Data type: `String` Array

Qualifiers: \[out\]

Logon names of the users.

`PermittedOperations` Data type: `UInt32` Array

Qualifiers: \[out\]

Granted permissions.

## Return Values

A `UInt32` data type that is 0 to indicate success or non-zero to indicate failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_RbacSecuredObject Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_rbacsecuredobject-server-wmi-class)
