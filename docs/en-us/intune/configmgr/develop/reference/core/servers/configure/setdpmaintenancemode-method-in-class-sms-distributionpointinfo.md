<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/setdpmaintenancemode-method-in-class-sms-distributionpointinfo -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SetDPMaintenanceMode method in class SMS\_DistributionPoint

The `SetDPMaintenanceMode` WMI class method in Configuration Manager sets a distribution point in maintenance mode. For more information, see [Maintenance mode](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_maint).

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```MOF
uint32 SetDPMaintenanceMode(
    [in] string NALPath,
    [in] uint32 Mode
);
```

## Parameters

### `NALPath`

Data type: `String`

Qualifiers: `[in]`

Network abstraction layer \(NAL\) path to the distribution point server.

### `Mode`

Data type: `uint32`

Qualifiers: `[in]`

`1` to enable maintenance mode, `0` to disable

## Return values

An `uint32` data type that's `0` indicates success. A non-zero hresult indicates failure.

For more information about handling returned errors, see [About Configuration Manager errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime requirements

For more information, see [Configuration Manager server runtime requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager server development requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See also

[SMS\_DistributionPointInfo Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpointinfo-server-wmi-class)
