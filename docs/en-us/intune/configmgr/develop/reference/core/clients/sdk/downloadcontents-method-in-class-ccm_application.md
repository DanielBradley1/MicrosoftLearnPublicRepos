<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/sdk/downloadcontents-method-in-class-ccm_application -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# DownloadContents Method in Class CCM\_Application

The `DownloadContents` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, that downloads the content for an application.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
uint32 DownloadContents
{
    [IN]    String Id
    [IN]    String Revision
    [IN]    Boolean IsMachineTarget
    [IN]    String Priority
    [OUT]   String JobId
};
```

## Parameters

`Id` Data type: `String`

Qualifiers: \[id\("0"\), in\]

Application identifier.

`Revision` Data type: `String`

Qualifiers: \[id\("1"\), in\]

Revision.

`IsMachineTarget` Data type: `Boolean`

Qualifiers: \[id\("2"\), in\]

`true` if the application targets a device.

`Priority` Data type: `String`

Qualifiers: \[id\("3"\), in, valuemap\]

Priority. Possible values are:

| Value |
| --- |
| Foreground |
| High |
| Normal |
| Low |

`JobId` Data type: `String`

Qualifiers: \[id\("4"\), out\]

Job identifier.

## Remarks

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
