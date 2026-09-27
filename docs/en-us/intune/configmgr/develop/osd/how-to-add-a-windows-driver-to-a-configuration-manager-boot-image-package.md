<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-windows-driver-to-a-configuration-manager-boot-image-package -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Add a Windows Driver to a Configuration Manager Boot Image Package

In Configuration Manager, you add a Windows driver to an operating system deployment boot image package by adding a reference to the required driver in the [SMS\_BootImagePackage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class) `ReferencedDrivers` array property.

Note

The `ReferencedDrivers` property is an array of an embedded [SMS\_Driver\_Details](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver_details-server-wmi-class) object, and you can add more than one driver to the package. The objects in the array are added to the boot image package each time it is updated on the distribution point.

The location of the driver content is usually obtained from the [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object `ContentSourcePath` property, but this can be overridden if the original driver location is not available.

It might be necessary to add network or storage drivers to a boot image package so that a task sequence can access the network and disk resources while in WinPE.

Drivers are added to the image only when the boot image is refreshed by calling the [RefreshPkgSource Method in Class SMS\_BootImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/refreshpkgsource-method-in-class-sms_bootimagepackage) method.

Drivers are added to the image by using Windows Package Manager.

### To add a Windows driver to a boot image package

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get the [SMS\_BootImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_bootimagepackage-server-wmi-class) object for the boot image package that you want to add the driver to.
3. Create and populate an embedded `SMS_Driver_Details` object to contain the driver details.
4. Add the `SMS_Driver_Details` object to the `ReferencedDrivers` array property of the `SMS_BootImagePackage` object.
5. Commit the `SMS_BootImagePackage` object changes.

## Example

The following example method adds a Windows driver to a boot image package. The package is identified by its `PackageID` property, and the driver is identified by its `CI_ID` property.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub AddDriverToBootImagePackage(connection, driverId,packageId)

    Dim bootImagePackage
    Dim driver
    Dim referencedDrivers
    Dim driverDetails

    ' Get the boot image package and referenced drivers.
    Set bootImagePackage = connection.Get("SMS_BootImagePackage.PackageID='" & packageId &"'" )
    referencedDrivers = bootImagePackage.ReferencedDrivers

    ' Get the driver.
    Set driver = connection.Get("SMS_Driver.CI_ID=" & driverId )

    ' Create and populate the driver details.
    Set driverDetails = connection.Get("SMS_Driver_Details").SpawnInstance_
    driverDetails.ID=driverId
    driverDetails.SourcePath=driver.ContentSourcePath

    ' Add the driver details.
    ReDim Preserve referencedDrivers (Ubound (referencedDrivers)+1)
    Set referencedDrivers(Ubound(referencedDrivers))=driverDetails
    bootImagePackage.ReferencedDrivers=referencedDrivers

    bootImagePackage.Put_
    bootImagePackage.RefreshPkgSource

End Sub
```

```c#
public void AddDriverToBootImagePackage(
    WqlConnectionManager connection,
    int driverId,
    string packageId)
{
    try
    {
        // Get the boot image package.
        IResultObject bootImagePackage = connection.GetInstance(@"SMS_BootImagePackage.packageId='" + packageId + "'");

        // Get the driver.
        IResultObject driver = connection.GetInstance("SMS_Driver.CI_ID=" + driverId);

        // Get the drivers that are referenced by the package.
        List<IResultObject> referencedDrivers = bootImagePackage.GetArrayItems("ReferencedDrivers");

        // Create and populate an embedded SMS_Driver_Details. This is added to the ReferencedDrivers array.
        IResultObject driverDetails = connection.CreateEmbeddedObjectInstance("SMS_Driver_Details");

        driverDetails["ID"].IntegerValue = driverId;
        driverDetails["SourcePath"].StringValue = driver["ContentSourcePath"].StringValue;

        // Add the driver details to the array.
        referencedDrivers.Add(driverDetails);

        // Add the array to the boot image package.
        bootImagePackage.SetArrayItems("ReferencedDrivers", referencedDrivers);

        // Commit the changes.
        bootImagePackage.Put();
        bootImagePackage.ExecuteMethod("RefreshPkgSource", null);
    }
    catch (SmsException e)
    {
        Console.WriteLine(e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed:`WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `driverID` | - Managed: `String`  <br>- VBScript: `String` | The Windows driver identifier available in `SMS_Driver.CI_ID`. |
| `PackageID` | - Managed: `String`  <br>- VBScript: `String` | The boot image package identifier available in `SMS_BootImagePackage.PackageID`. |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/role-based-administration).

## See Also

[About Operating System Deployment Driver Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-driver-management) [How to Remove a Windows Driver from a Boot Image Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-remove-a-windows-driver-from-a-boot-image-package)
