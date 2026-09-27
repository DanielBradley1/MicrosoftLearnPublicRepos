<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-driver-management -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# About Operating System Deployment Driver Management

In Configuration Manager, the driver catalog helps manage the cost and complexity of deploying an operating system in an environment that contains different types of computers and devices. By storing device drivers in the driver catalog and not with each individual operating system image, the number of operating system images that is needed is greatly reduced. For more information about the driver catalog, see [Manage drivers](https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/manage-drivers).

Note

Before a driver can be used, it must be added to a driver package. For more information, see [How to Create a Driver Package for a Windows Driver in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-driver-package-for-a-windows-driver).

## Driver Catalog Management

With the Configuration Manager Operating System Deployment server Windows Management Instrumentation \(WMI\) classes you can manage the following:

- Driver import
- Driver packages
- Boot images
- Supported platforms

### Driver Import

Using the [SMS\_Driver](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) import methods, you can import the Windows drivers described by .inf and Txtsetup.oem files into the driver catalog. For more information, see [How to Import a Windows Driver Described by an INF File into Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-import-a-windows-driver-described-by-an-inf-file) and [How to Import a Windows Driver Described by an OEM File into Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-import-a-windows-driver-described-by-a-txtsetup-oem-file).

Before a driver can be used, it must be enabled. For more information, see [How to Enable or Disable a Windows Driver in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-enable-or-disable-a-windows-driver).

### Driver Packages

Driver packages contain one or more Windows drivers. A driver package is an `SMS_DriverPackage` object and is distributed in the same way as an `SMS_Package` package. They both derive from [SMS\_PackageBaseClass](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_packagebaseclass-server-wmi-class).

For more information about creating a driver package, see [How to Create a Driver Package for a Windows Driver in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-driver-package-for-a-windows-driver).

### Boot Images

Windows device drivers that have been imported into the driver catalog can be added to one or more boot images. Boot images are stored in [SMS\_BootImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class) objects. In an `SMS_BootImagePackage` object, Windows drivers are kept in an array of referenced drivers. For more information, see [How to add a Windows Driver to a Configuration Manager Boot Image Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-windows-driver-to-a-configuration-manager-boot-image-package)

### Supported Platforms

Windows drivers can be configured to support specific platforms. The supported platforms are stored in the driver package XML. For more information, see [How to Specify The Supported Platforms for a Driver](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-specify-the-supported-platforms-for-a-driver).

### Driver Categories

You can associate categories with Windows device drivers. For more information, see [How to Add a Category to a Windows Driver](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-category-to-a-windows-driver)
