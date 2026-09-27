<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Add a Configuration Manager Context Qualifier by Using WMI

In Configuration Manager, you add context qualifiers to a connection \([SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices)\) or object \([SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject)\) by creating a [SWbemNamedValueSet](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemnamedvalueset) value set to hold the context qualifiers. You then provide the [SWbemNamedValueSet](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemnamedvalueset) value set as a parameter to connection and object methods.

in Configuration Manager, you can provide your application name \(ApplicationName\), computer name \(MachineName\) and locale identifier \(LocaleID\).

In most cases, context qualifiers are not required. The main exception is accessing the site control file where they are needed to set up session information. For more information, see [About the Configuration Manager Site Control File](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file).

### To add a Configuration Manager context qualifier

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Create a [WbemScripting.SWbemNamedValueSet](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemnamedvalueset) object and add the desired context qualifiers.
3. Use the [SWbemNamedValue](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemnamedvalue) value set you created in step two to pass context qualifiers to connection and object manipulation calls.

## Example

The following VBScript example creates a [SWbemNamedValueSet](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemnamedvalueset) value set and adds the supplied context qualifiers. The following code example demonstrates how to call the method for use in an [SMS\_Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) package object **Put** method call. For more information about Configuration Manager objects, see [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview).

`Dim context`

`Set context = CreateContextQualifiers("My application" , "My Computer" , "MS\1033")`

`package.Put_ , context`

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs

Function CreateContextQualifiers(applicationName, machineName, localeID)
    On Error Resume next
    Dim smsContext

    set smsContext = CreateObject("WbemScripting.SWbemNamedValueSet")

    ' Add the context qualifiers to the set.
    smsContext.Add "LocaleID", localeID
    smsContext.Add "MachineName", machineName
    smsContext.Add "ApplicationName", applicationName

    Set CreateContextQualifiers = smsContext

      If Err.Number<>0 Then
        WScript.Echo Err.Description
        CreateContextQualifiers = null
        Exit Function
    End If
End Function
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `applicationName` | - `String` | The ApplicationName context qualifier. |
| `machineName` | - `String` | The computer name qualifier. |
| `localeID` | - `String` | The locale identifier. For example, MS\\1033 is English \(U.S.\). If you need the locale for non-U.S. installations, you can get it from the [SMS\_Identification Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class)`LocaleID` property. |

## Compiling the Code

This VBScript example requires:

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/role-based-administration).

## See Also

[About the Configuration Manager Site Control File](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [Configuration Manager Context Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/context-qualifiers) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [Windows Management Instrumentation](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page)
