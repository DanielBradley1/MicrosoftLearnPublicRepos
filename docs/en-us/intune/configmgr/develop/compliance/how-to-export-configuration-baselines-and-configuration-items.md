<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/how-to-export-configuration-baselines-and-configuration-items -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Export Configuration Baselines and Configuration Items

In Configuration Manager, to export a configuration baseline or configuration item using the Configuration Manager SDK, read the relevant `SMS_ConfigurationItem` instance and write the `SDMPackageXML` property \(string\) to a file.

Important

The encoding of the XML file must be set to UTF-16 encoded Unicode.

### To export Configuration Baselines and Configuration Items

1. Set up a connection to the SMS Provider.
2. Get the specific instance of [SMS\_ConfigurationItem](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class) class using the unique ID of the configuration item \(CI\_ID\).
3. Copy the configuration item XML \(SDMPackageXML\) into a variable.
4. Write the configuration item XML content to a file.

## Example

The following code example shows how to read an instance of a configuration baseline or configuration item and then export it to a file.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs

Sub DCMExportBaselineOrCI(swbemServices, _
                          pathToFile,    _
                          configurationItemId)

' Set required variables.
fileContents          =    ""
configurationItemXML  =    null

' Get specified configuration item (configurationItemId variable).
Set getCIInfo = swbemServices.Get("SMS_ConfigurationItem.CI_ID=" & configurationItemId )

' Copy configuration item XML into variable.
configurationItemXML = getCIInfo.SDMPackageXML

Wscript.Echo configurationItemXML

' Open file for write (Unicode option enabled by second true).
Set FSO = CreateObject("Scripting.FileSystemObject")
Set textFile = FSO.CreateTextFile(pathToFile, true, true)

' Write XML content to file specified by pathToFile.
textFile.Write configurationItemXML
textFile.Close

Wscript.Echo " "
Wscript.Echo "Successfully wrote " & pathToFile

End Sub
```

```c#

public void DCMExportBaselineOrCI(WqlConnectionManager connection,
                                  string pathToOutputFile,
                                  string configurationItemId)
{

    // Set required variables.
    string configurationItemXML = null;

    try
    {
        // Get the specified configuration item (configurationItemId variable).
        IResultObject getCIInfo = connection.GetInstance(@"SMS_ConfigurationItem.CI_ID=" + configurationItemId);

        // Copy configuration item XML into variable.
        configurationItemXML = getCIInfo["SDMPackageXML"].StringValue;
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to retrieve configuration item xml. " + "\n" + ex.Message);
        throw;
    }

    StreamWriter sw = null;
    try
    {
        // Open file for output.
        sw = new StreamWriter(pathToOutputFile, false, System.Text.Encoding.Unicode);

        // Write XML to output file.
        sw.Write(configurationItemXML);
    }
    catch (Exception ex)
    {
        Console.WriteLine("Failed to write configuration item XML to: " + pathToOutputFile + "\n" + ex.Message);
        throw;
    }
    finally
    {
        if (sw != null)
        {
            sw.Close();
        }
    }

    Console.WriteLine("Wrote configuration item XML to: " + pathToOutputFile);
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| - pathToOutputFile  <br>- pathToFile | - Managed: `String`  <br>- VBScript: `String` | Path to the output file. |
| `configurationItemId` | - Managed: `String`  <br>- VBScript: `String` | Identifier of a configuration item to export. |

## Compiling the Code

### Namespaces

System

System.Collections.Generic

System.ComponentModel

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

[About Configuration Baselines and Configuration Items](https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/about-configuration-baselines-and-configuration-items) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Connect to a Configuration Manager Provider using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Connect to a Configuration Manager Provider Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [SMS\_BaselineAssignment Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_baselineassignment-server-wmi-class) [SMS\_ConfigurationItem Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_configurationitem-server-wmi-class)
