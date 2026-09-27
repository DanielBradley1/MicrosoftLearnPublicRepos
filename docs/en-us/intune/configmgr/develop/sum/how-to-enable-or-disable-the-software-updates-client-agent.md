<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-enable-or-disable-the-software-updates-client-agent -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Enable or Disable the Software Updates Client Agent

You enable or disable the Software Updates Client Agent, in Configuration Manager, by modifying the site control file settings.

### To enable or disable the Software Updates Client Agent

1. Set up a connection to the SMS Provider.
2. Make a connection to the Software Updates Client Agent section of the site control file by using the [SMS\_SCI\_ClientComp](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the changes to the site control file.

## Example

The following example method enables or disables the Software Updates Client Agent by using the [SMS\_SCI\_ClientComp](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class to connect to the site control file and change properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs

Sub EnableDisableSUMClientAgent(swbemServices,     _
                                swbemContext,      _
                                enableDisableFlag, _
                                siteToChange )

    ' Load site control file and get software updates client component section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteToChange & """", "Refresh", , , swbemContext
    Set objSWbemInst = swbemServices.Get("SMS_SCI_ClientComp.Filetype=1,Itemtype='Client Component',Sitecode='" & siteToChange & "',ItemName='Software Updates'", , swbemContext)

    ' Display the Software Updates Client Agent settings before changing the properties.
    Wscript.Echo " "
    Wscript.Echo "Properties - Before Change"
    Wscript.Echo "---------------------------"
    Wscript.Echo objSWbemInst.ClientComponentName
    Wscript.Echo objSWbemInst.Flags & " (0 = Disabled, 1 = Enabled)"

    ' Set Software Updates Client Agent by setting Flags value to 0 or 1 by using the enableDisableFlag variable.
    objSWbemInst.Flags = enableDisableFlag

    ' Save new Software Updates Client Agent settings.
    objSWbemInst.Put_ , swbemContext
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteToChange & """", "Commit", , , swbemContext

    ' Refresh in-memory copy of the site control file and get the software updates client component section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteToChange & """", "Refresh", , , swbemContext
    Set objSWbemInst = swbemServices.Get("SMS_SCI_ClientComp.Filetype=1,Itemtype='Client Component',Sitecode='" & siteToChange & "',ItemName='Software Updates'", , swbemContext)

    ' Display the Software Updates Client Agent settings after changing the properties.
    Wscript.Echo " "
    Wscript.Echo "Properties - After Change"
    Wscript.Echo "---------------------------"
    Wscript.Echo objSWbemInst.ClientComponentName
    Wscript.Echo objSWbemInst.Flags & " (0 = Disabled, 1 = Enabled)"

End Sub
```

```c#

public void EnableDisableSUMClientAgent(WqlConnectionManager connection,
                                        string enableDisableFlag,
                                        string siteCode)
{
    try
    {
        IResultObject siteDefinition = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Software Updates'");

        // Display Software Updates Client Agent settings before changing the properties.
        Console.WriteLine();
        Console.WriteLine("Properties - Before Change");
        Console.WriteLine("---------------------------");
        Console.WriteLine(siteDefinition["ClientComponentName"].StringValue);
        Console.WriteLine(siteDefinition["Flags"].StringValue + " (0 = Disabled, 1 = Enabled)");

        // Set Software Updates Client Agent by setting "Flags" value to 0 or 1 by using the enableDisableFlag variable.
        siteDefinition["Flags"].StringValue = enableDisableFlag;

        // Save the settings.
        siteDefinition.Put();

        // Verify the change by reconnecting and getting the value again.
        IResultObject siteDefinition2 = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Software Updates'");

        // Display Software Updates Client Agent settings after changing the properties.
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
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `swbemContext` | - VBScript: `SWbemContext` | A valid context object. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi). |
| `siteCode` | - Managed: `String` | The site code. |
| `siteToChange` | - VBScript: `String` | The site code. |
| `enableDisableFlag` | - Managed: `String`  <br>- VBScript: `String` | Determines whether the Software Updates Client Agent is enabled or disabled.  <br>  <br>0 - Disabled  <br>  <br>1 - Enabled |

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

[About Software Updates Setup and Configuration](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-software-updates-setup-and-configuration) [About the Configuration Manager Site Control File](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file) [How to Read and Write to the Configuration Manager Site Control File by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-managed-code) [How to Read and Write to the Configuration Manager Site Control File by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-wmi) [SMS\_SCI\_Component Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_component-server-wmi-class) [How to Add a Configuration Manager Context Qualifier by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi)
