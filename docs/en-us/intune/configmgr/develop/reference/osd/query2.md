<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/query2 -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Query2

`Query2` specifies a query, in Configuration Manager, that is used to identify the platform that a client computer is running.

Note

This information should come from `SMS_SupportedPlatforms Server WMI Class` objects and match the platform information specified in the PlatformApplicabilityCondition node.

The query is run on the client computer and typically inspects Windows Management Instrumentation \(WMI\) to determine the client platform. For example, `SELECT * FROM Win32_Processor WHERE Architecture=9 AND DataWidth=64`.

**Type**: Element.

**Instances**: One.

## Attributes

None

## See Also

[Operating System Deployment Driver Supported Platforms Schema](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/operating-system-deployment-driver-supported-platforms-schema) [PlatformApplicabilityCondition](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/platformapplicabilitycondition) [Query1](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/query1)
