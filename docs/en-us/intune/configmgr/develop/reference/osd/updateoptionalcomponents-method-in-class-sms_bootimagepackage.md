<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/updateoptionalcomponents-method-in-class-sms_bootimagepackage -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# UpdateOptionalComponents Method in Class SMS\_BootImagePackage

The `UpdateOptionalComponents` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, updates all specified optional components to the boot image package.

Note

It is necessary to refresh the distribution points when using this method.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 UpdateOptionalComponents(
      String ComponentIds[],
);
```

#### Parameters

`ComponentIds` Data type: `String` Array

Qualifiers: \[in\]

Component identifiers. The following are possible values:

| ID value | WinPE component |
| --- | --- |
| X86 |  |
| 1 | WinPE-DismCmdlets.cab |
| 2 | WinPE-Dot3Svc.cab |
| 3 | WinPE-EnhancedStorage.cab |
| 4 | WinPE-FMAPI.cab |
| 5 | WinPE-FontSupport-JA-JP.cab |
| 6 | WinPE-FontSupport-KO-KR.cab |
| 7 | WinPE-FontSupport-ZH-CN.cab |
| 8 | WinPE-FontSupport-ZH-HK.cab |
| 9 | WinPE-FontSupport-ZH-TW.cab |
| 10 | WinPE-HTA.cab |
| 11 | WinPE-StorageWMI.cab |
| 12 | WinPE-LegacySetup.cab |
| 13 | WinPE-MDAC.cab |
| 14 | WinPE-NetFx4.cab |
| 15 | WinPE-PowerShell3.cab |
| 16 | WinPE-PPPoE.cab |
| 17 | WinPE-RNDIS.cab |
| 18 | WinPE-Scripting.cab |
| 19 | WinPE-SecureStartup.cab |
| 20 | WinPE-Setup.cab |
| 21 | WinPE-Setup-Client.cab |
| 22 | WinPE-Setup-Server.cab |
| 23 | Not used. |
| 24 | WinPE-WDS-Tools.cab |
| 25 | WinPE-WinReCfg.cab |
| 26 | WinPE-WMI.cab |

| ID value | WinPE component |
| --- | --- |
| X64 |  |
| 27 | WinPE-DismCmdlets.cab |
| 28 | WinPE-Dot3Svc.cab |
| 29 | WinPE-EnhancedStorage.cab |
| 30 | WinPE-FMAPI.cab |
| 31 | WinPE-FontSupport-JA-JP.cab |
| 32 | WinPE-FontSupport-KO-KR.cab |
| 33 | WinPE-FontSupport-ZH-CN.cab |
| 34 | WinPE-FontSupport-ZH-HK.cab |
| 35 | WinPE-FontSupport-ZH-TW.cab |
| 36 | WinPE-HTA.cab |
| 37 | WinPE-StorageWMI.cab |
| 38 | WinPE-LegacySetup.cab |
| 39 | WinPE-MDAC.cab |
| 40 | WinPE-NetFx4.cab |
| 41 | WinPE-PowerShell3.cab |
| 42 | WinPE-PPPoE.cab |
| 43 | WinPE-RNDIS.cab |
| 44 | WinPE-Scripting.cab |
| 45 | WinPE-SecureStartup.cab |
| 46 | WinPE-Setup.cab |
| 47 | WinPE-Setup-Client.cab |
| 48 | WinPE-Setup-Server.cab |
| 49 | Not used. |
| 50 | WinPE-WDS-Tools.cab |
| 51 | WinPE-WinReCfg.cab |
| 52 | WinPE-WMI.cab |

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Remarks

It is not necessary to refresh the distribution points when using this method.

For more information about NAL paths, see [SMS\_NAL\_Methods Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_nal_methods-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class) [SMS\_NAL\_Methods Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_nal_methods-server-wmi-class)
