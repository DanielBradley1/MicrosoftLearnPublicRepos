<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/geteula-method-in-class-sms_softwareupdate -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetEULA Method in Class SMS\_SoftwareUpdate

The `GetEULA` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the localized Microsoft Software License Terms content of a configuration item.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetEULA(
     String EULA
);
```

#### Parameters

`EULA` Data type: `String`

Qualifiers: \[out\]

The Microsoft Software License Terms.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

Your application should call this method only if the `EulaExists` property is set to `true` in the configuration item for the software update. This property is defined in the [SMS\_ConfigurationItemBaseClass Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitembaseclass-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class)
