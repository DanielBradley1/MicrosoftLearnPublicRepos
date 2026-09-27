<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/setignoreprereqwarning-method-in-class-sms_cm_updatepackages -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# SetIgnorePrereqWarning Method in Class SMS\_CM\_UpdatePackages

The `SetIgnorePrereqWarning` Windows Management Instrumentation \(WMI\) class method in Configuration Manager updates the ignore prerequisites warning flag of the update packages.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method:

## Syntax

```
SInt32 SetIgnorePrereqWarning(
     UInt32 flag
);
```

#### Parameters

`flag` Data type: `UInt32`

Qualifiers: \[in\]

Flag to ignore the prerequisites warning flag of the update packages. Possible values are:

| Value | Flag |
| --- | --- |
| 0 | NOT\_CONTINUE\_ON\_PREREQ\_WARNING. During installation, stop the upgrade if there's a prerequisite warning. |
| 1 | PREREQ\_ONLY. Run only the prerequisite. |
| 2 | CONTINUE\_ON\_PREREQ\_WARNING. During installation, ignore the prerequisite warning. |

## Return Values

An `SInt32` data type that is 0 to indicate success or nonzero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_CM\_UpdatePackages Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackages-server-wmi-class)
