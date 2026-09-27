<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Perform a Synchronous Configuration Manager Query by Using WMI

In Configuration Manager, you perform a synchronous query for Configuration Manager objects by calling the [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) object [ExecQuery](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices-execquery) method and passing a WQL query.

A synchronous query is a query that maintains control over the process of your application for the duration of the query. A synchronous query has the potential of locking up your application for large queries or for queries over a network. Alternatively, you can run an asynchronous query that returns control to the application while the query is run. For more information, see [How to Perform an Asynchronous Configuration Manager Query by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-query-by-using-managed-code)

Note

Lazy properties are not returned in synchronous queries. For more information, see [How to Read Lazy Properties by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi).

### To perform a synchronous query

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).
2. Using the SWbemServices object that you obtain from step one, use the ExecQuery method to get a [SWbemObjectSet](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobjectset) collection containing the query results.
3. Iterate through the SWbemObjectSet collection to access a [SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject) for each object returned by the query.

## Example

The following example performs a synchronous query of all packages in Configuration Manager.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub QueryPackages(connection)

    On Error Resume next

    Dim packages
    Dim package

    ' Run the query.
    Set packages = _
        connection.ExecQuery("Select * From SMS_Package")

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get Packages"
        Wscript.Quit
    End If

    For Each package In packages
        WScript.Echo  package.Name
    Next

    If packages.Count=0 Then
        Wscript.Echo "No packages found"
    End If

End Sub
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

## See Also

[Windows Management Instrumentation](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Call a Configuration Manager Object Class Method by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [How to Create a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-wmi) [How to Delete a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-wmi) [How to Modify a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-wmi) [How to Perform an Asynchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-configuration-manager-query-by-using-wmi) [How to Read a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-wmi) [How to Read Lazy Properties by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi) [Configuration Manager Extended WMI Query Language](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/extended-wmi-query-language) [Configuration Manager Result Sets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/result-sets) [Configuration Manager Special Queries](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/special-queries) [About queries](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-queries)
