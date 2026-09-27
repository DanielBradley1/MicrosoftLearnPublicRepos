<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-set-software-updates-branding-information -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Set Software Updates Branding Information

You set the Software Updates client branding information, in Configuration Manager, by modifying the necessary site control file settings.

### To set software updates client branding information

1. Set up a connection to the SMS Provider.
2. Make a connection to the Client Agent section of the site control file by using the [SMS\_SCI\_ClientComp](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class.
3. Loop through the array of available properties, making changes as needed.
4. Commit the changes to the site control file.

## Example

The following example sets the Software Updates client branding information by using the [SMS\_SCI\_ClientComp](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_clientcomp-server-wmi-class) class to connect to the site control file and change properties. This example changes the Software Updates subheading information displayed in the client user interface in notifications or reminders.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs

Sub SetSUMBranding(swbemServices,          _
                   swbemContext,           _
                   siteCode,               _
                   brandingText)

    ' Load site control file and get the client agent section.
    swbemServices.ExecMethod "SMS_SiteControlFile.Filetype=1,Sitecode=""" & siteCode & """", "Refresh", , , swbemContext

    Query = "SELECT * FROM SMS_SCI_ClientComp " & _
            "WHERE ClientComponentName = 'Client Agent' " & _
            "AND SiteCode = '" & siteCode & "'"

    Set SCIComponentSet = swbemServices.ExecQuery(Query, ,wbemFlagForwardOnly Or wbemFlagReturnImmediately, swbemContext)

    ' Only one instance is returned from the query.
    For Each SCIComponent In SCIComponentSet

        ' Loop through the array of embedded SMS_EmbeddedProperty instances.
        For Each vProperty In SCIComponent.Props

            ' Setting: SUMBrandingSubTitle
            If vProperty.PropertyName = "SUMBrandingSubTitle" Then
                wscript.echo " "
                wscript.echo vProperty.PropertyName
                wscript.echo "Current value " &  vProperty.Value1

                ' Modify the value.
                vProperty.Value1 = brandingText
                wscript.echo "New value: " & brandingText
            End If

        Next

             ' Update the component in your copy of the site control file. Get the path
             ' to the updated object, which could be used later to retrieve the instance.
              Set SCICompPath = SCIComponent.Put_(wbemChangeFlagUpdateOnly, swbemContext)
    Next

    ' Commit the change to the actual site control file.
    Set InParams = swbemServices.Get("SMS_SiteControlFile").Methods_("CommitSCF").InParameters.SpawnInstance_
    InParams.SiteCode = siteCode
    swbemServices.ExecMethod "SMS_SiteControlFile", "CommitSCF", InParams, , swbemContext

End Sub
```

```c#

public void SetSUMClientBranding(WqlConnectionManager connection,
                                 string siteCode,
                                 string brandingText)
{
    try
    {
        // Get the site control file client component section.
        IResultObject clientAgent = connection.GetInstance(@"SMS_SCI_ClientComp.FileType=1,ItemType='Client Component',SiteCode='" + siteCode + "',ItemName='Client Agent'");

        // Load the embedded properties into a temporary copy.
        Dictionary<string, IResultObject> tempEmbeddedProperties = clientAgent.EmbeddedProperties;

        // Update the branding information with the string variable passed in.
        tempEmbeddedProperties["SUMBrandingSubTitle"]["Value1"].StringValue = brandingText;

        // Replace the embedded properties object with the temporary copy.
        clientAgent.EmbeddedProperties = tempEmbeddedProperties;

        // Commit the change back to the site control file.
        clientAgent.Put();
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to set branding text: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `swbemContext` | - VBScript: `SWbemContext` | A valid context object. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi). |
| `siteCode` | - Managed: `String`  <br>- VBScript: `String` | The site code. |
| `brandingText` | - Managed: `String`  <br>- VBScript: `String` | The text to replace the branding text in the site control file. |

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
