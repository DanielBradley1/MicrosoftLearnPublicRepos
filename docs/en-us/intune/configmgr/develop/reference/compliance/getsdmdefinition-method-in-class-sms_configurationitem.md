<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/getsdmdefinition-method-in-class-sms_configurationitem -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetSDMDefinition Method in Class SMS\_ConfigurationItem

The `GetSDMDefinition` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, retrieves the System Definition Model \(SDM\) definition of the configuration item in XML format.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetSDMDefinition(
     String SDMDefinition
);
```

#### Parameters

`SDMDefinition` Data type: `String`

Qualifiers: \[out\]

The SDM definition in XML format.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

For more information about SDM definitions, see About Authoring Configuration Baselines and Configuration Items.

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_ConfigurationItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class)
