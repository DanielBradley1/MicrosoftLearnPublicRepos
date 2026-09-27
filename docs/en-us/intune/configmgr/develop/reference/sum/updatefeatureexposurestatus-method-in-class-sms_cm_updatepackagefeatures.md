<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/updatefeatureexposurestatus-method-in-class-sms_cm_updatepackagefeatures -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# UpdateFeatureExposureStatus Method in Class SMS\_CM\_UpdatePackageFeatures

The `UpdateFeatureExposureStatus` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, updates the feature exposure status for an update package feature extension.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
 SInt32 UpdateFeatureExposureStatus(  
     UInt32 Status  
);  
```

#### Parameters

`Status`  
Data type: `uint32`

Qualifiers: \[in\]

The installation state.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_CM\_UpdatePackageFeatures Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackagefeatures-server-wmi-class)
