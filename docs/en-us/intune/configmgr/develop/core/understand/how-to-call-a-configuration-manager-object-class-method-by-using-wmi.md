<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Call a Configuration Manager Object Class Method by Using WMI

To call a SMS Provider class method, in Configuration Manager, you use the [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) object [ExecMethod](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices-execmethod) method to call methods that are defined by the class.

Note

To call a method on an object instance, call the method from the object directly. For example, `ObjectInstance.MethodName parameters`.

### To call a Configuration Manager object class method

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Using the SWbemServices you obtain in step one, call [Get](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices-get) to get the class definition.
3. Create the input parameters as a [SWbemMethodSet](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemmethodset).
4. Using the SWbemServices object instance, call [ExecMethod](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices-execmethod) and specify the class name and input parameters.
5. Retrieve the method return value from the *ReturnValue* property in the returned [SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject) object.

## Example

The following example validates a collection rule query by calling the [SMS\_CollectionRuleQuery](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionrulequery-server-wmi-class) class [ValidateQuery](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/validatequery-method-in-class-sms_collectionrulequery) class method.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub ValidateQueryRule(connection, wqlQuery)

    Dim inParams
    Dim outParams
    Dim collectionRuleClass

    On Error Resume Next

    ' Obtain the class definition object of a SMS_CollectionRuleQuery object.
    Set collectionRuleClass = connection.Get("SMS_CollectionRuleQuery")

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get collection rule query object"
        Exit Sub
    End If

    ' Set up the in parameter.
    Set inParams = collectionRuleClass.Methods_("ValidateQuery").InParameters.SpawnInstance_
    inParams.WQLQuery = wqlQuery
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get in parameters object"
        Exit Sub
    End If

    ' Call the method.
    Set outParams = _
        connection.ExecMethod( "SMS_CollectionRuleQuery", "ValidateQuery", inParams)
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't run method"
        Exit Sub
    End If

    If outParams.ReturnValue = True Then
        Wscript.Echo "Valid query"
    Else
        WScript.Echo "Not a valid query"
    End If
  End Sub
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `wqlQuery` | - `String` | A WQL query string. For this example, `SELECT * FROM SMS_R_System` is a valid query. |

## Compiling the Code

## See Also

[Windows Management Instrumentation](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [How to Create a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-wmi) [How to Delete a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-delete-a-configuration-manager-object-by-using-wmi) [How to Modify a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-wmi) [How to Perform an Asynchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-configuration-manager-query-by-using-wmi) [How to Perform a Synchronous Configuration Manager Query by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi) [How to Read a Configuration Manager Object by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-wmi) [How to Read Lazy Properties by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-wmi)
