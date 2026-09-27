<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/userhaspermissions-method-in-class-sms_rbacsecuredobject -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# UserHasPermissions Method in Class SMS\_RbacSecuredObject

The `UserHasPermissions` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, determines whether the current user has the requested permissions for the specified object.

The following syntax is simplified from Managed Object Format \(MOF\) code and is intended to show the definition of the method.

## Syntax

```
Boolean UserHasPermissions(
     ref:SMS_BaseClass ObjectPath,
     UInt32 Permissions,
);
```

#### Parameters

`ObjectPath` Data type: `ref:SMS_BaseClass`

Qualifiers: \[in\]

Object being checked for access permissions, which can be a class name or instance path.

`Permissions` Data type: `UInt32`

Qualifiers: \[in,out\]

The permission the user has on the object specified by `ObjectPath`.

Possible values are defined by the properties of `SMS_SecuredObject Server WMI Class`.

## Return Values

Returns a `Boolean` data type that is `true` if the user has permissions.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_RbacSecuredObject Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_rbacsecuredobject-server-wmi-class)
