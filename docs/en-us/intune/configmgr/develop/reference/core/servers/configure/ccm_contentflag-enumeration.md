<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ccm_contentflag-enumeration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_CONTENTFLAG Enumeration

The **CCM\_CONTENTFLAG** enumeration contains options for transferring content.

## Syntax

```vb
typedef enum
{
    CCM_CONTENTFLAG_LOCAL_ONLY                  = 0x00000001,
    CCM_CONTENTFLAG_REMOTE_ONLY                 = 0x00000002,
    CCM_CONTENTFLAG_LOCAL_OR_REMOTE             = 0x00000004,
    CCM_CONTENTFLAG_PROTECTED_ONLY              = 0x00000008,
    CCM_CONTENTFLAG_ALLOW_CACHING               = 0x00000010,
    CCM_CONTENTFLAG_PEERDP                      = 0x00000020,
    CCM_CONTENTFLAG_REMOTE_NOLOCALPEERDP        = 0x00000040,
    CCM_CONTENTFLAG_DELTA_DOWNLOAD              = 0x00000080,
    CCM_CONTENTFLAG_ALLOW_ALTERNATE_PROVIDERS   = 0x00000100
}
CCM_CONTENTFLAG;
```

## Members

| Content flag | Description |
| --- | --- |
| CCM\_CONTENTFLAG\_LOCAL\_ONLY | Local only. |
| CCM\_CONTENTFLAG\_REMOTE\_ONLY | Remote only. |
| CCM\_CONTENTFLAG\_LOCAL\_OR\_REMOTE | Local or remote. |
| CCM\_CONTENTFLAG\_PROTECTED\_ONLY | Protected only. |
| CCM\_CONTENTFLAG\_ALLOW\_CACHING | Allow caching. |
| CCM\_CONTENTFLAG\_PEERDP | Branch distribution point. |
| CCM\_CONTENTFLAG\_REMOTE\_NOLOCALPEERDP | No local branch distribution point. |
| CCM\_CONTENTFLAG\_DELTA\_DOWNLOAD | Delta download. |
| CCM\_CONTENTFLAG\_ALLOW\_ALTERNATE\_PROVIDERS | Allow alternate providers. |

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
