<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/clearcontexthandle-method-in-class-sms_contextmethods -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ClearContextHandle Method in Class SMS\_ContextMethods

The `ClearContextHandle` method, in Configuration Manager, clears cached context data that is associated with the specified context handle.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 ClearContextHandle(
   String ContextHandle
);
```

## Parameter

`ContextHandle` Data type: `String`

Qualifiers: \[in\]

Context handle resulting from a call to the [GetContextHandle Method in Class SMS\_ContextMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/getcontexthandle-method-in-class-sms_contextmethods).

## Return Values

An `SInt32` data type that indicates 0 for success, or non-zero for failure.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ContextMethods Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_contextmethods-server-wmi-class) [GetContextHandle Method in Class SMS\_ContextMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/getcontexthandle-method-in-class-sms_contextmethods)
