<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ccm_dts_priority-enumeration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CCM\_DTS\_PRIORITY enumeration

The **CCM\_DTS\_PRIORITY** enumeration indicates the priority of the download.

## Syntax

```
typedef enum
{
    CCM_DTS_PRIORITY_FOREGROUND,
    CCM_DTS_PRIORITY_HIGH,
    CCM_DTS_PRIORITY_NORMAL,
    CCM_DTS_PRIORITY_LOW,
}CCM_DTS_PRIORITY;
```

## Members

| Priority flag | Description |
| --- | --- |
| CCM\_DTS\_PRIORITY\_FOREGROUND | The highest priority. |
| CCM\_DTS\_PRIORITY\_HIGH | High priority. |
| CCM\_DTS\_PRIORITY\_NORMAL | Normal priority. |
| CCM\_DTS\_PRIORITY\_LOW | Low priority. |

## Remarks

The only strict requirement is that jobs at a lower priority do not block progress of jobs at a higher priority. Providers must respect this.

## Requirements

### Runtime requirements

For more information, see [Configuration Manager client runtime requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements).

### Development requirements

For more information, see [Configuration Manager client development requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements).
