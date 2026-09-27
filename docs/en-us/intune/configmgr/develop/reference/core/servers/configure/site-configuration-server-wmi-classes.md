<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/site-configuration-server-wmi-classes -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Site configuration server WMI classes

This section contains detailed reference information about the site configuration server WMI classes in Configuration Manager. These classes include classes that relate to an installation of Configuration Manager that consists of one or more computers running the Configuration Manager components.

You can configure the components of a site at any time to enhance the management of your site. Configuration information is contained in the install map and the site control file.

When you install Configuration Manager, it creates an install map that describes the initial configuration of the installed features for the server, client, and Configuration Manager console. The install map configuration data is read-only and uses the following classes:

- [SMS\_SiteInstallMap Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallmap-server-wmi-class)
- [SMS\_SiteInstallItemBase Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitembase-server-wmi-class)
- [SMS\_SiteInstallItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_siteinstallitem-server-wmi-class)
- [SMS\_SystemResourceList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_systemresourcelist-server-wmi-class)

Classes that are derived from `SMS_SiteInstallItem` use the naming convention `SMS_SII_*`**.** Classes that are derived from `SMS_SiteInstallItemBase` use the naming convention `SMS_SIIB_*`.

The site control file describes the current configuration of the site and its components. Use the following classes to manage the site control file and the site configuration data:

- [SMS\_SiteControlFile Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolfile-server-wmi-class)
- [SMS\_SiteControlItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sitecontrolitem-server-wmi-class)

Classes that are derived from `SMS_SiteControlItem` use the naming convention `SMS_SCI_*`. Use these classes to access and modify the configuration items that are contained in the site control file. For information about managing the site control file and changing component configuration, see [About the site control file](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file).
