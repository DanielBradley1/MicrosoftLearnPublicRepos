<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/operating-system-deployment-driver-supported-platforms-schema -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Operating System Deployment Driver Supported Platforms Schema

The following reference section documents the XML schema that is used to specify the platforms that are supported by an operating system deployment driver in Microsoft Configuration Manager.

The schema is used in the `SMS_Driver` class `SDMPackageXML` property.

Caution

The supported platforms portion of `SDMPackageXML` is the only part of the Driver XML schema that can be edited. You should not make changes to other parts of the XML.

## Supported Platform XML

<[PlatformApplicabilityConditions](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/platformapplicabilityconditions)>

<[PlatformApplicabilityCondition](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/platformapplicabilitycondition)>

<[Query1](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/query1)></Query1>

<[Query2](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/query2)></Query2>

</PlatformApplicabilityCondition>

</PlatformApplicabilityConditions>

## See Also

[Operating System Deployment Driver Supported Platforms Schema](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/operating-system-deployment-driver-supported-platforms-schema) [PlatformApplicabilityCondition](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/platformapplicabilitycondition) [Query1](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/query1) [Query2](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/query2)
