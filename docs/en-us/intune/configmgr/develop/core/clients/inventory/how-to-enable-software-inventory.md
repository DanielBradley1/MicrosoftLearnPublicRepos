<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/inventory/how-to-enable-software-inventory -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Enable Software Inventory

You enable or disable the Software Inventory Client Agent, in Configuration Manager, by modifying the site control file settings.

### To enable or disable the Software Inventory Updates Client Agent

1. Set up a connection to the SMS Provider.
2. Make a connection to the Software Inventory Client Agent section of the site control file by using the [SMS\_SCI\_ClientComp](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the changes to the site control file.

## Example

The following example method enables or disables the Software Inventory Client Agent by using the [SMS\_SCI\_ClientComp](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class to connect to the site control file and change properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs

Sub EnableDisableSoftwareInventoryClientAgent(swbemServices, swbemContext, enableDisableFlag, siteCode )  

    ' Load site control file and get software inventory agent client component section.  
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext  
    Set objSWbemInst = swbemServices.Get("SMS_SCI_ClientComp.Filetype=1,Itemtype='Client Component',Sitecode='" & siteCode & "',ItemName='Software Inventory Agent'", , swbemContext)  

    ' Display client agent settings before changing the properties.  
    Wscript.Echo " "  
    Wscript.Echo "Properties - Before Change"  
    Wscript.Echo "---------------------------"  
    Wscript.Echo objSWbemInst.ClientComponentName  
    Wscript.Echo objSWbemInst.Flags & " (0 = Disabled, 1 = Enabled)"  

    ' Set client agent by setting the Flags value to  0 or 1 using the enableDisableFlag variable.  
    objSWbemInst.Flags = enableDisableFlag  

    ' Save the new client agent settings.  
    objSWbemInst.Put_ , swbemContext  
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Commit", , , swbemContext  

    ' Refresh in-memory copy of the site control file and get the client component section.  
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext  
    Set objSWbemInst = swbemServices.Get("SMS_SCI_ClientComp.Filetype=1,Itemtype='Client Component',Sitecode='" & siteCode & "',ItemName='Software Inventory Agent'", , swbemContext)  

    ' Display the client agent settings after change.  
    Wscript.Echo " "  
    Wscript.Echo "Properties - After Change"  
    Wscript.Echo "---------------------------"  
    Wscript.Echo objSWbemInst.ClientComponentName  
    Wscript.Echo objSWbemInst.Flags & " (0 = Disabled, 1 = Enabled)"  

End Sub  
```

```c#

public void EnableDisableSoftwareInventoryClientAgent(WqlConnectionManager connection,  
                                                      string enableDisableFlag,  
                                                      string siteCode)  
{  
    try  
    {  
        IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Software Inventory Agent'");  

        // Display client agent settings before changing the properties.  
        Console.WriteLine();  
        Console.WriteLine("Properties - Before Change");  
        Console.WriteLine("---------------------------");  
        Console.WriteLine(siteDefinition["ClientComponentName"].StringValue);  
        Console.WriteLine(siteDefinition["Flags"].StringValue + " (0 = Disabled, 1 = Enabled)");  

        // Set client agent by setting "Flags" value to 0 or 1 by using the enableDisableFlag variable.  
        siteDefinition["Flags"].StringValue = enableDisableFlag;  

        // Save the settings.  
        siteDefinition.Put();  

        // Verify the change by reconnecting and getting the value again.  
        IResultObject siteDefinition2 = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Software Inventory Agent'");  

        // Display client agent settings after changing the properties.  
        Console.WriteLine();  
        Console.WriteLine("Properties - After Change");  
        Console.WriteLine("--------------------------");  
        Console.WriteLine(siteDefinition2["ClientComponentName"].StringValue);  
        Console.WriteLine(siteDefinition2["Flags"].StringValue + " (0 = Disabled, 1 = Enabled)");  
    }  

    catch (SmsException ex)  
    {  
        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);  
        throw;  
    }  

}  
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| - `connection`  <br>- `swbemServices` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `swbemContext` | - VBScript: `SWbemContext` | A valid context object. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi). |
| `siteCode` | - Managed: `String`  <br>- VBScript: `String` | The site code. |
| `enableDisableFlag` | - Managed: `String`  <br>- VBScript: `String` | Determines whether the Software Inventory client agent is enabled or disabled.  <br>  <br>0 - Disabled  <br>  <br>1 - Enabled |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/role-based-administration).

## See Also

[Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk)  
[About Configuration Manager Inventory](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/inventory/about-configuration-manager-inventory)  
[About the Configuration Manager Site Control File](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file)  
[How to Read and Write to the Configuration Manager Site Control File by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-managed-code)  
[How to Read and Write to the Configuration Manager Site Control File by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-wmi)  
[SMS\_SCI\_Component Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_component-server-wmi-class)
