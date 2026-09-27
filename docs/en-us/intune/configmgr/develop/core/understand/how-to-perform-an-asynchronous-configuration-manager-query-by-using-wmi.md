<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-configuration-manager-query-by-using-wmi -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Perform an Asynchronous Configuration Manager Query by Using WMI

In Configuration Manager, you perform a synchronous query for Configuration Manager objects by calling the [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) object [ExecQueryAsync](https://learn.microsoft.com/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-execqueryasync) method and by implementing a sink method to handle query results.

To handle each returned object, create an [objWbemSink.OnObjectReady](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemsink-onobjectready) event subroutine. To be notified when the query is completed, create a [objWbemSink.OnCompleted](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemsink-oncompleted) event subroutine.

Note

Lazy properties are not returned in asynchronous queries. For more information, see [How to Read Lazy Properties by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi).

### To perform an asynchronous query

1. Set up a connection to the SMS Provider. For more information, see [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi).
2. Create an [OnObjectReady](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemsink-onobjectready) subroutine to handle objects by the query.
3. Create an [OnCompleted](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemsink-oncompleted) subroutine to handle query completion.
4. Using the [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) object you obtain from step one, use [ExecQueryAsync](https://learn.microsoft.com/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-execqueryasync) object to query Configuration Manager objects asynchronously.

## Example

The following VBScript code example asynchronously queries for all [SMS\_Collection](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) objects.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Dim bdone
Sub QueryCollection(connection)

    Dim sink
    bdone = False

    Set sink = WScript.CreateObject("wbemscripting.swbemsink","sink_")

    ' Query for all collections.
    connection.ExecQueryAsync sink, "select * from SMS_Collection"

    ' Wait until all instances are returned.
    While Not bdone
        wscript.sleep 1000
    Wend
 End Sub

' The sink subroutine to handle the OnObjectReady
' event. This is called as each object returns.
Sub sink_OnObjectReady(collection, octx)
    WScript.Echo "CollectionID: " + collection.CollectionID
    WScript.Echo "Name: " + collection.Name
    Wscript.Echo
End Sub

' The sink subroutine to handle the OnCompleted event.
' This is called when all the objects are returned.
' The oErr parameter obtains an SWbemLastError object,
' if available from the provider.
Sub sink_OnCompleted(HResult, oErr, oCtx)
    WScript.Echo "All collections returned"
    bdone = true
End Sub
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

## See Also

[Windows Management Instrumentation](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Call a Configuration Manager Object Class Method by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [How to Create a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-wmi) [How to Delete a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-wmi) [How to Modify a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-wmi) [How to Perform a Synchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi) [How to Read a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-wmi) [How to Read Lazy Properties by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi) [Configuration Manager Extended WMI Query Language](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/extended-wmi-query-language) [Configuration Manager Result Sets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/result-sets) [Configuration Manager Special Queries](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/special-queries) [About queries](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-queries)
