<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/updateprereqandstateflags-method-in-class-sms_cm_updatepackages -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# UpdatePrereqAndStateFlags Method in Class SMS\_CM\_UpdatePackages

The `UpdatePrereqAndStateFlags` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, updates the installation state of update packages.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 UpdatePrereqAndStateFlags(  
     UInt32 flag,  
     UInt32 state  
);  
```

#### Parameters

`flag`  
Data type: `UInt32`

Qualifiers: \[in\]

Pre-requisites flag for an update package. Possible values are:

| Value | Description |
| --- | --- |
| 0 | NOT\_CONTINUE\_ON\_PREREQ\_WARNING. During installation, stop the upgrade if there is a prerequisite warning. |
| 1 | PREREQ\_ONLY. Run only the prerequisite. |
| 2 | CONTINUE\_ON\_PREREQ\_WARNING. During installation, ignore the prerequisite warning. |

`state`  
Data type: `UInt32`

Qualifiers: \[in\]

Installation state of an update package. Possible values are:

| Value | Installation state |
| --- | --- |
| 0x2 | ENABLED |
| 0x00040001 | DOWNLOAD\_IN\_PROGRESS |
| 0x00040002 | DOWNLOAD\_SUCCESS |
| 0x0004FFFF | DOWNLOAD\_FAILED |
| 0x00050001 | APPLICABILITY\_CHECKING |
| 0x00050002 | APPLICABILITY\_SUCCESS |
| 0x0005FFFD | APPLICABILITY\_HIDE |
| 0x0005FFFE | APPLICABILITY\_NA |
| 0x0005FFFF | APPLICABILITY\_FAILED |
| 0x00010001 | CONTENT\_REPLICATING |
| 0x00010002 | CONTENT\_REPLICATION\_SUCCESS |
| 0x0001FFFF | CONTENT\_REPLICATION\_FAILED |
| 0x00020001 | PREREQ\_IN\_PROGRESS |
| 0x00020002 | PREREQ\_SUCCESS |
| 0x00020003 | PREREQ\_WARNING |
| 0x0002FFFF | PREREQ\_ERROR |
| 0x00030001 | INSTALL\_IN\_PROGRESS |
| 0x00030002 | INSTALL\_WAITING\_SERVICE\_WINDOW |
| 0x00030003 | INSTALL\_WAITING\_PARENT |
| 0x00030004 | INSTALL\_SUCCESS |
| 0x00030005 | INSTALL\_PENDING\_REBOOT |
| 0x0003FFFF | INSTALL\_FAILED |
| 0x00030006 | INSTALL\_CMU\_VALIDATING |
| 0x00030007 | INSTALL\_CMU\_STOPPED |
| 0x00030008 | INSTALL\_CMU\_INSTALLFILES |
| 0x00030009 | INSTALL\_CMU\_STARTED |
| 0x0003000A | INSTALL\_CMU\_SUCCESS |
| 0x0003000B | INSTALL\_WAITING\_CMU |
| 0x0003FFFE | INSTALL\_CMU\_FAILED |
| 0x0003000C | INSTALL\_INSTALLFILES |
| 0x0003000D | INSTALL\_UPGRADESITECTRLIMAGE |
| 0x0003000E | INSTALL\_CONFIGURESERVICEBROKER |
| 0x0003000F | INSTALL\_INSTALLSYSTEM |
| 0x00030010 | INSTALL\_CONSOLE |
| 0x00030011 | INSTALL\_INSTALLBASESERVICES |
| 0x00030012 | INSTALL\_UPDATE\_SITES |
| 0x00030013 | INSTALL\_SSB\_ACTIVATION\_ON |
| 0x00030014 | INSTALL\_UPGRADEDATABASE |
| 0x00030015 | INSTALL\_UPDATEADMINCONSOLE |

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_CM\_UpdatePackages Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_cm_updatepackages-server-wmi-class)
