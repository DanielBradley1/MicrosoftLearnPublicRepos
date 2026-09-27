<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_contextmethods-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2024-01-18 -->

# SMS\_ContextMethods Server WMI Class

The `SMS_ContextMethods` Windows Management Instrumentation \(WMI\) class is an abstract class in Configuration Manager that contains methods for caching WMI context qualifiers with the SMS Provider.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_ContextMethods ();
```

## Methods

The following table lists the methods in `SMS_ContextMethods`.

| Term | Description |
| --- | --- |
| [ClearContextHandle Method in Class SMS\_ContextMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/clearcontexthandle-method-in-class-sms_contextmethods) | Releases cached context data. |
| [GetContextHandle Method in Class SMS\_ContextMethods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/getcontexthandle-method-in-class-sms_contextmethods) | Caches multiple context qualifiers within the SMS Provider. This allows applications to use a much smaller context object when making API calls to WMI. |

## Properties

The `SMS_ContextMethods` class doesn't define any properties.

## Remarks

Class qualifiers for this class include:

- Abstract

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Context Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/context-qualifiers)
