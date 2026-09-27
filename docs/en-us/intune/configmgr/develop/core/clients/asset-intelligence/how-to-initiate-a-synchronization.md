<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/asset-intelligence/how-to-initiate-a-synchronization -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Initiate a Synchronization

The Asset Intelligence catalog can be refreshed manually, outside the normal synchronization schedule. A manual refresh is accomplished by using the [RequestCatalogUpdate](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/requestcatalogupdate-method-in-class-sms_aiproxy) method on the [SMS\_AIProxy Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aiproxy-server-wmi-class).

Important

This method can only be called once within a 12 hours period, subsequent method calls will not work.

### Refresh the Asset Intelligence catalog

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Query the SMS Provider for the [SMS\_AIProxy](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/sms_aiproxy-server-wmi-class) instance that you want refresh the catalog on.
3. Call the SMS\_AIProxy class [RequestCatalogUpdate](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/asset-intelligence/requestcatalogupdate-method-in-class-sms_aiproxy) method to run an action on the collection.

## Example

The following example method runs the refresh on the provided server.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Function InitiateSync(connection, serverName)
    On Error Resume Next    
    Dim classObj: Set classObj = connection.Get("SMS_AIProxy")    
    Dim inParams: Set inParams = classObj.Methods_("RequestCatalogUpdate").InParameters.SpawnInstance_()
    Dim outParams
    inParams.Properties_.Item("ProxyName") = serverName
    Set outParams = connection.ExecMethod("SMS_AIProxy", "RequestCatalogUpdate", inParams)
    If Err.Number <> 0 Then
        InitiateSync = False
    Else
        InitiateSync = True
    End If
    On Error Goto 0
End Function  
```

```c#
public void InitiateSync(WqlConnectionManager connection, string serverName)
{
    try
    {        
        Dictionary<string, object> inParams = new Dictionary<string, object>();
        IResultObject classObj = connection.GetClassObject("SMS_AIProxy");
        inParams.Add("ProxyName", serverName);
        Console.WriteLine("Requesting catalog update on server " + serverName);
        classObj.ExecuteMethod("RequestCatalogUpdate", inParams);    
    }    
    catch (SmsException ex)    
    {        
        Console.WriteLine(String.Format("Failed to request catalog update on server {0}. Error: {1}", serverName, ex.Message));           
        throw;    
    }
}  
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| connection | Managed: `WqlConnectionManager`  <br>  <br>VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the provider. |
| serverName | Managed: `String`  <br>  <br>VBScript: `String` | Name of the server to run the refresh on. This name maps to the `ProxyName` property of an `SMS_AIProxy` instance. |

## Compiling the Code

The C# example requires:

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
