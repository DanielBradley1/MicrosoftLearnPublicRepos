<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-wmi -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Modify a Configuration Manager Object by Using WMI

You modify a Configuration Manager object, in Configuration Manager, by using the object's [SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject) object to change its properties.

### To modify a Configuration Manager object

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).
2. Using the [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) object you obtain from step one, call the [Get](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices-get) method and specify the class and key information for the object you want. This returns a [SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject) representing object.
3. Using the [SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject), update the object properties.
4. Call [Put\_](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject-put-) to update the object in the SMS Provider.

## Example

The following VBScript code example gets a package \(SMS\_Package\) object, changes the package description, and then commits the changes back to the SMS Provider. In this example, the package is retrieved through a call to the SWbemServices object [Get](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices-get). You can also retrieve the package by using a query. For more information, see [How to Perform a Synchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub ModifyPackageDescription (connection, packageID, description)

    On Error Resume Next
    Dim package

    ' Get the package.
    Set package = connection.Get("SMS_Package.PackageID='" & packageID & "'")
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get package " + packageID
        Exit Sub
    End If

    Wscript.Echo "Package Name: " + package.Name
    Wscript.Echo "Current Description: " + package.Description

    ' Update and commit the package.
    package.Description = description

    package.Put_
    If Err.Number<>0 Then
        WScript.Echo "Couldn't commit the package"
        Exit Sub
    End If

    Wscript.Echo "New Description: " + package.Description
End Sub
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `packageID` | `String` | The package identifier. This is available from the `SMS_Package` class `PackageID` identifier. |
| `Description` | `String` | A new description for the object. |

## See Also

[Windows Management Instrumentation](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Call a Configuration Manager Object Class Method by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [How to Create a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-wmi) [How to Delete a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-wmi) [How to Perform an Asynchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-configuration-manager-query-by-using-wmi) [How to Perform a Synchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi) [How to Read a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-wmi) [How to Read Lazy Properties by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi)
