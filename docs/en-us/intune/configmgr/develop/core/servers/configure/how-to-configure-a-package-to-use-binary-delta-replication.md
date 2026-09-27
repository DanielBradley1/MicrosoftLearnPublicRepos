<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-configure-a-package-to-use-binary-delta-replication -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Configure a Package to Use Binary Delta Replication

The following example shows how to configure an existing package to use binary delta replication, in Configuration Manager, by using the `SMS_Package` class and the `PkgFlags` class property.

### To configure an existing package to use binary delta replication

1. Set up a connection to the SMS Provider.
2. Load the existing package object using `SMS_Package` class.
3. Modify the `PkgFlags` using the hexadecimal value for AP\_USE\_BINARY\_DELTA\_REP.
4. Save the package and the new package properties.

## Example

The following example method configures an existing package to use binary delta replication.

Important

The hexadecimal values that define the `PkgFlags` property are listed in the `SMS_Package` class reference material.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs

Sub ModifyPackageToUseBinaryDeltaReplication(connection, existingPackageID)

    ' Define a constant with the hexadecimal value for AP_USE_BINARY_DELTA_REP.
    Const AP_USE_BINARY_DELTA_REP = &H04000000

    ' Get the specific advertisement instance to modify.     Dim packageToModify
    Set packageToModify = connection.Get("SMS_Package.PackageID='" & existingPackageID & "'")

    ' List the existing property values.
    Wscript.Echo " "
    Wscript.Echo "Values before change: "
    Wscript.Echo "--------------------- "
    Wscript.Echo "Package Name:   " & packageToModify.Name
    Wscript.Echo "Package Flags:  " & packageToModify.PkgFlags

    ' Set the new property value.
    packageToModify.PkgFlags = packageToModify.PkgFlags OR AP_USE_BINARY_DELTA_REP

    ' Save the advertisement.
    packageToModify.Put_

    ' Output the new property values.
    Wscript.Echo " "
    Wscript.Echo "Values after change: "
    Wscript.Echo "--------------------- "
    Wscript.Echo "Package Name:   " & packageToModify.Name
    Wscript.Echo "Package Flags:  " & packageToModify.PkgFlags

End Sub
```

```c#

public void ModifyPackageToUseBinaryDeltaReplication(WqlConnectionManager connection, string existingPackageID)
{
    // Define a constant with the hexadecimal value for AP_USE_BINARY_DELTA_REP.
    const Int32 AP_USE_BINARY_DELTA_REP = 0x04000000;

    try
    {
        // Get the specific package instance to modify.
        IResultObject packageToModify = connection.GetInstance(@"SMS_Package.PackageID='" + existingPackageID + "'");

        // List the existing property values.
        Console.WriteLine();
        Console.WriteLine("Values before change:");
        Console.WriteLine("_____________________");
        Console.WriteLine("Package Name:  " + packageToModify["Name"].StringValue);
        Console.WriteLine("Package Flags: " + packageToModify["PkgFlags"].IntegerValue);

        // Modify the PkgFlags value to include the AP_USE_BINARY_DELTA_REP value.
        packageToModify["PkgFlags"].IntegerValue = packageToModify["PkgFlags"].IntegerValue | AP_USE_BINARY_DELTA_REP;

        // Save the package with the new value.
        packageToModify.Put();

        // Reload the package to verify the change.
        packageToModify.Get();

        // List the existing (modified) property values.
        Console.WriteLine();
        Console.WriteLine("Values after change:");
        Console.WriteLine("_____________________");
        Console.WriteLine("Package Name:  " + packageToModify["Name"].StringValue);
        Console.WriteLine("Package Flags: " + packageToModify["PkgFlags"].IntegerValue);
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to modify package. Error: " + ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection`  <br>  <br>`swbemServices` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingPackageID` | - Managed: `String`  <br>- VBScript: `String` | The ID of the existing package. |

## Compiling the Code

The C# example requires:

### Namespaces

System

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

mscorlib

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## .NET Framework Security

## See Also

[Software distribution overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/software-distribution-overview) [SMS\_SCI\_Component Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_component-server-wmi-class)
