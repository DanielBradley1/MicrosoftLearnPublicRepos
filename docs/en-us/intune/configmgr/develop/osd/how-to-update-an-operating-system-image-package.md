<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-update-an-operating-system-image-package -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Update an Operating System Image Package in Configuration Manager

In Configuration Manager, you update the Windows Image \(WIM\) file that is associated with the operating system package by calling the image package's [SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imagepackage-server-wmi-class) class instance [ReloadImageProperties](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/reloadimageproperties-method-in-class-sms_imagepackage) method. The image is updated based on the location defined in the `pkgSourcePath` property.

### To update an operating system image package

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get the `SMS_ImagePackage` class instance you want to update.
3. Call the `ReloadImageProperties` class instance method.
4. Commit the `SMS_ImagePackage` class instance.

## Example

The following example updates an operating system image package.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub UpdateOSImage(connection,imagePackageID, sourcePath)

    Dim imagePackage

    ' Get the image.
    set imagePackage = connection.Get("SMS_ImagePackage.PackageID='" & imagePackageID & "'")

    ' Update the source.
    imagePackage.PkgSourcePath=sourcePath
    imagePackage.Put_
    imagePackage.RefreshPkgSource

End Sub
```

```c#
public void UpdateOSImage(
    WqlConnectionManager connection,
    string imagePackageId,
    string sourcePath)
{
    try
    {
        // Get the image package.
        IResultObject imagePackage = connection.GetInstance(@"SMS_ImagePackage.PackageID='" + imagePackageId + "'");

        // Update the location.
        imagePackage["PkgSourcePath"].StringValue = sourcePath;
        imagePackage.Put();
        imagePackage.ExecuteMethod("RefreshPkgSource", null);
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
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `imagePackageID` | - Managed: `String`  <br>- VBScript: `String` | The package image identifier. It is available from `SMS_ImagePackage. PackageID`. |
| `sourcePath` | - Managed: `String`  <br>- VBScript: `String` | The path to the image package source in Universal Naming Convention \(UNC\) format. |

## Compiling the Code

The C# example has the following compilation requirements:

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

## See also

[About image management](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-image-management)
