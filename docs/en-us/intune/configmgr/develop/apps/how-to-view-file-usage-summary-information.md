<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-view-file-usage-summary-information -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to View File Usage Summary Information

You view file usage summary information, in Configuration Manager, by using the [SMS\_MeteredFiles](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_meteredfiles-server-wmi-class) and [SMS\_FileUsageSummary](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_fileusagesummary-server-wmi-class) classes.

### To view file usage summary information

1. Set up a connection to the SMS Provider.
2. Get a collection of all of the metered files [SMS\_MeteredFiles](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_meteredfiles-server-wmi-class).
3. Get a collection of all of the summarized files [SMS\_FileUsageSummary](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_fileusagesummary-server-wmi-class).
4. Loop through the summarized file information, displaying information as required.

## Example

The following example method displays file usage summary information by using the [SMS\_MeteredFiles](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_meteredfiles-server-wmi-class) and [SMS\_FileUsageSummary](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_fileusagesummary-server-wmi-class) classes.

Note

The example code below is relatively inefficient. In an environment with large amounts of data \(large result sets\), it would be better to do the query on SMS\_MeteredFiles, then loop over that result, doing individual queries for SMS\_FileUsageSummary where SMS\_FileUsageSummary.FileID=meteredFile.FileID.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs

sub ViewFileUsageSummaryInfo(connection)

' Get SMS_MeteredFiles - used to match FileID to a file name

' Build query to get all metered files.
meteredFilesQuery = "SELECT * FROM SMS_MeteredFiles"

' Run query.
Set meteredFiles = connection.ExecQuery(meteredFilesQuery, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

' Get the summarized files.

' Build query to get all file usage summary information.
fileUsageSummaryQuery = "SELECT * FROM SMS_FileUsageSummary"

' Run query.
Set fileUsageSummary = connection.ExecQuery(fileUsageSummaryQuery, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

' Output file usage summary information.
For Each summariedFile in fileUsageSummary

    For each meteredFile in meteredFiles

        if meteredFile.MeteredFileID=summariedFile.FileID then
            wscript.echo "File Name: " & meteredFile.FileName
            Exit For
        end if

    next

    ' As matching summary information is found, output details.
    wscript.echo "File ID: "             & summariedFile.FileID
    wscript.echo "Distinct User Count: " & summariedFile.DistinctUserCount
    wscript.echo "Interval Start: "      & summariedFile.IntervalStart
    wscript.echo "Interval Width: "      & summariedFile.IntervalWidth
    wscript.echo "Site Code: "           & summariedFile.SiteCode
    wscript.echo " "

Next

end sub
```

```c#

public void ViewFileUsageSummaryInfo(WqlConnectionManager connection)
{
    try
    {
        // Build query to get all metered files.
        string meteredFilesQuery = "SELECT * FROM SMS_MeteredFiles";

        // Run meteredFiles query.
        IResultObject meteredFilesTemp = connection.QueryProcessor.ExecuteQuery(meteredFilesQuery);

        // Cache values to local list.
        List<IResultObject> meteredFiles = new List<IResultObject>();
        foreach (IResultObject meteredFileTemp in meteredFilesTemp)
        {
            meteredFiles.Add(meteredFileTemp);
        }

        // Build query to get all the file usage summary information.
        string fileUsageSummaryQuery = "SELECT * FROM SMS_FileUsageSummary";

        // Run fileUsageSummary query.
        IResultObject fileUsageSummaryTemp = connection.QueryProcessor.ExecuteQuery(fileUsageSummaryQuery);

        // Cache values to local list.
        List<IResultObject> fileUsageSummary = new List<IResultObject>();
        foreach (IResultObject summariedFileTemp in fileUsageSummaryTemp)
        {
            fileUsageSummary.Add(summariedFileTemp);
        }

        // Enumerate through the files.
        foreach (IResultObject summariedFile in fileUsageSummary)
        {
            foreach (IResultObject meteredFile in meteredFiles)
            {
                if (meteredFile["MeteredFileID"].StringValue == summariedFile["FileID"].StringValue)
                {
                    // As matching summary information is found, output details.
                    Console.WriteLine("File Name: " + meteredFile["MeteredFileName"].StringValue);
                    break;
                };
            };

            // As matching summary information is found, output details.
            Console.WriteLine("File ID: " + summariedFile["FileID"].StringValue);
            Console.WriteLine("Distinct User Count: " + summariedFile["DistinctUserCount"].StringValue);
            Console.WriteLine("Interval Start: " + summariedFile["IntervalStart"].StringValue);
            Console.WriteLine("Interval Width: " + summariedFile["IntervalWidth"].StringValue);
            Console.WriteLine("Site Code: " + summariedFile["SiteCode"].StringValue);
            Console.WriteLine(" ");
        };
    }
    catch (SmsException ex)
    {
        Console.WriteLine();
        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

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

[Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk) [About the Configuration Manager Site Control File](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file) [How to Read and Write to the Configuration Manager Site Control File by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-managed-code) [How to Read and Write to the Configuration Manager Site Control File by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-wmi) [SMS\_SCI\_Component Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_component-server-wmi-class)
