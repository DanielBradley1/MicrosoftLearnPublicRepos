<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-wmi -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Delete a Configuration Manager Object by Using WMI

To delete a Configuration Manager object, in Configuration Manager, call the [SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject) object [Delete\_](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject-delete-) method.

### To delete a Configuration Manager object

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).
2. Using the [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) object you obtain from step one, call the [Get](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices-get) method and specify the class and key information for the object you want to delete. `Get` returns a `SWbemObject` that represents the object.
3. Using the `SWbemObject`, call `Delete` to delete the object.

## Example

The following VBScript code example deletes the package \([SMS\_Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class)\) identified by its package identifier `packageID`.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub DeletePackage (connection, packageID)

    On Error Resume Next
    Dim package

    Set package = connection.Get("SMS_Package.PackageID='" & packageID & "'")
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get package " + packageID
        Exit Sub
    End If

    package.Delete_

    WScript.Echo "Package deleted"

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't delete " + packageID
        Exit Sub
    End If

End Sub
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | `SWbemServices` | A valid connection to the SMS Provider. |
| `packageID` | `String` | The package identifier. This is obtained from the `SMS_Package` class `PackageID`. |

## See Also

[Windows Management Instrumentation](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Call a Configuration Manager Object Class Method by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [How to Create a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-wmi) [How to Modify a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-wmi) [How to Perform an Asynchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-configuration-manager-query-by-using-wmi) [How to Perform a Synchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi) [How to Read a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-wmi) [How to Read Lazy Properties by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi)
