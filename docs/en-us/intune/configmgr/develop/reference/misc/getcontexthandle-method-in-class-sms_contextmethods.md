<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/getcontexthandle-method-in-class-sms_contextmethods -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetContextHandle Method in Class SMS\_ContextMethods

The `GetContextHandle` method, in Configuration Manager, stores context objects on the server.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetContextHandle(
      String ContextHandle
);
```

#### Parameters

`ContextHandle` Data type: `String`

Qualifiers: \[out\]

Context handle that identifies the cached context object on the server.

## Return Values

An `SInt32` data type that indicates 0 for success or non-zero for failure.

## Remarks

Use this method to replace the contents of your context object with the object indicated by the retrieved context handle. Storing context object data on the server saves network bandwidth for client applications that repeatedly call the SMS Provider using a large number of context qualifiers or a large amount of qualifier data.

For a complete description of the steps required to use this optimization technique, see the ContextHandle qualifier in [Configuration Manager Context Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/context-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ContextMethods Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_contextmethods-server-wmi-class) [ClearContextHandle](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/clearcontexthandle-method-in-class-sms_contextmethods)
