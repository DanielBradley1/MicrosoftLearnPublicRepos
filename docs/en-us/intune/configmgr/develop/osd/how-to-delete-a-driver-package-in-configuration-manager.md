<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-delete-a-driver-package-in-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Delete a Driver Package in Configuration Manager

You delete an operating system deployment driver package, in Configuration Manager, by deleting its [SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driverpackage-server-wmi-class) object.

Note

Windows drivers that are referenced by the driver package are not deleted.

### To delete a driver package

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get the [SMS\_DriverPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driverpackage-server-wmi-class) object for the driver that you want to delete.
3. Delete the SMS\_DriverPackage object.

## Example

The following example method deletes a driver package identified by its package identifier.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub DeleteDriverPackage(connection,packageID)

        ' Get the driver.
        Set driverPackage = connection.Get("SMS_DriverPackage.PackageID='" & packageID & "'")

        ' Delete the driver package.
        driverPackage.Delete_

End Sub
```

```c#
public void DeleteDriverPackage(
    WqlConnectionManager connection,
    string packageId)
{
    try
    {
        // Get the driver package.
        IResultObject driverPackage = connection.GetInstance("SMS_DriverPackage.packageId='" + packageId + "'");

        // Delete the driver package.
        driverPackage.Delete();
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to delete driver package: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed:`WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `packageID` | - Managed: `String`  <br>- VBScript: `String` | - The driver package identifier available in SMS\_DriverDriverPackage.PackageID. |

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
