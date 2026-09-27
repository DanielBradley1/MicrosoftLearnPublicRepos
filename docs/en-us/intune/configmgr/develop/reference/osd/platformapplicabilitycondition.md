<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/platformapplicabilitycondition -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# PlatformApplicabilityCondition

`PlatformApplicabilityCondition` specifies one supported platform for an operating system deployment driver in Configuration Manager.

Note

It is only valid to populate this information with values from `SMS_SupportedPlatforms Server WMI Class` objects. Drivers can be targeted only at major releases, for example, all Windows.

**Type**: String.

**Instances**: Zero or more.

## Attributes

| Attribute | Description |
| --- | --- |
| DisplayName | The platform name displayed in the Configuration Manager console. |
| MaxVersion | The maximum supported version. For example, "5.20.9999.9999". |
| MinVersion | The minimum supported version. For example, "5.20.3790.0". |
| Name | The operating system name. For example, "Windows NT". |
| Platform | The supported platform, for example, "x64". |

## See Also

[Operating System Deployment Driver Supported Platforms Schema](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/operating-system-deployment-driver-supported-platforms-schema) [PlatformApplicabilityConditions](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/platformapplicabilityconditions) [Query1](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/query1) [Query2](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/query2)
