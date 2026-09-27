<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ccm_dts_flag-enumeration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_DTS\_FLAG Enumeration

The **CCM\_DTS\_FLAG** enumeration indicates special options on download jobs.

## Syntax

```
typedef enum
{
    CCM_DTS_FLAG_SINGLEFILE             = 0x00000001,
    CCM_DTS_FLAG_DIRECTORY              = 0x00000002,
    CCM_DTS_FLAG_NOTIFYPROGRESS         = 0x00000004,
    CCM_DTS_FLAG_INSECURETRANSPORT      = 0x00000008,
    CCM_DTS_FLAG_TOPLEVELFILESONLY      = 0x00000010,
    CCM_DTS_FLAG_SENDAUTHHEADERS        = 0x00000020,
    CCM_DTS_FLAG_SENDAUTHHEADERS_MIXED  = 0x00000040,
    CCM_DTS_FLAG_USEINPUTMANIFEST       = 0x00000080,
    CCM_DTS_FLAG_SKIPHOSTCHANGEHANDLING = 0x00000100
}
CCM_DTS_FLAG;
```

## Members

| CTS flag | Description |
| --- | --- |
| CCM\_DTS\_FLAG\_SINGLEFILE | Reserved. |
| CCM\_DTS\_FLAG\_DIRECTORY | Indicates that `szRemotePath` is a directory and that all of its contents should be downloaded. This should always be specified in the case of alternate providers. |
| CCM\_DTS\_FLAG\_NOTIFYPROGRESS | This indicates that progress notifications are required. Even if this flag is not specified, success and error notifications are still required. |
| CCM\_DTS\_FLAG\_INSECURETRANSPORT | Reserved. |
| CCM\_DTS\_FLAG\_TOPLEVELFILESONLY | Reserved. |
| CCM\_DTS\_FLAG\_SENDAUTHHEADERS | Reserved. |
| CCM\_DTS\_FLAG\_SENDAUTHHEADERS\_MIXED | Reserved. |
| CCM\_DTS\_FLAG\_USEINPUTMANIFEST | Reserved. |
| CCM\_DTS\_FLAG\_SKIPHOSTCHANGEHANDLING | Reserved. |

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
