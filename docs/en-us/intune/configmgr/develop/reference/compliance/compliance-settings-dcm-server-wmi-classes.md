<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# About compliance settings server WMI classes

In Configuration Manager, compliance settings server WMI classes assist you in assessing computer compliance. You can consider a number of configurations, for example, installation and configuration of the correct versions of Windows operating systems. You can also use these classes to check for compliance with software updates and security settings.

The main classes supporting the compliance settings feature are:

- [SMS\_ConfigurationItem server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class), representing a generic configuration item.
- [SMS\_ConfigurationBaselineInfo server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationbaselineinfo-server-wmi-class), representing information for a baseline configuration item.
- [SMS\_BaselineAssignment server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class), representing an assignment of a baseline configuration item.

For more information, see [About configuration baselines and configuration items](https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/about-configuration-baselines-and-configuration-items).

Note

Some of the classes for compliance settings, for example, [SMS\_ConfigurationBaselineInfo server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationbaselineinfo-server-wmi-class), are specific to baseline configuration items. Some of the classes can also be used to reference software update configuration items, although applications use the software updates feature to manipulate these items. For more information, see [About software update deployments](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-software-updates-deployments).

The Configuration Manager server class schema is a set of WMI classes that represent the objects on a server running Configuration Manager. Each Configuration Manager class is a template for a managed object and all instances of the object use the template. Classes can contain properties and methods. The properties describe the class data, and the methods typically perform data management. For more information about developing applications using these classes, see [About Configuration Manager SDK requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/about-configuration-manager-sdk-requirements).
