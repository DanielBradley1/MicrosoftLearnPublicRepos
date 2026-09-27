<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_nal_methods-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_NAL\_Methods Server WMI Class

The `SMS_NAL_Methods` Windows Management Instrumentation \(WMI\) class, in Configuration Manager, defines and manipulates a network abstraction layer \(NAL\) path.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_NAL_Methods : SMS_BaseClass ();
```

## Methods

The following table lists the methods in `SMS_NAL_Methods`.

| Method | Description |
| --- | --- |
| [PackNALPath](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/packnalpath-method-in-class-sms_nal_methods) | Encodes a NAL path from its components. |
| [UnPackNALPath](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/unpacknalpath-method-in-class-sms_nal_methods) | Decodes a NAL path into its components. |

## Properties

The `SMS_NAL_Methods` class does not define any properties.

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

[SMS\_DistributionPoint Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpoint-server-wmi-class) [SMS\_SCI\_SysResUse Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_sysresuse-server-wmi-class) [SMS\_SystemResourceList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_systemresourcelist-server-wmi-class)
