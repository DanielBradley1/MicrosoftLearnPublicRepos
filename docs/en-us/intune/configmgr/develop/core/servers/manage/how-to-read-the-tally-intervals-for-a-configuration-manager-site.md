<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-read-the-tally-intervals-for-a-configuration-manager-site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Read the Tally Intervals for a Configuration Manager Site

In Configuration Manager, you can read the available tally intervals for a site by inspecting the site control file `SMS_COMPONENT_STATUS_SUMMARIZER` object `Summary_Intervals` embedded property list.

You use tally intervals for querying component \(`SMS_ComponentSummarizer`\) and site detail \(`SMS_SiteDetailSummarizer`\) summarizer classes. For more information, see [About Configuration Manager Status Summarizers](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-summarizers).

### To read the tally intervals for a site

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Perform a query for the site's SMS\_COMPONENT\_STATUS\_SUMMARIZER property lists
3. In the results from step two, search for the Summary\_Intervals embedded property list.
4. Display the contents of the embedded property list.

## Example

The following example method returns a [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) object after importing it from the supplied XML.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub ShowSiteTallyIntervals(connection, siteCode)

    Dim SCIComponent              'SMS_SCI_Component class
    Dim SCIComponentSet         'Enumeration of SMS_SCI_Component
    Dim query
    Dim i
    Dim vProperty                     'Embedded property

    query = "SELECT PropLists FROM SMS_SCI_Component " & _
            "WHERE ComponentName = 'SMS_COMPONENT_STATUS_SUMMARIZER' " & _
            "AND SiteCode = '" + siteCode + "'"

    ' You do not need to get a copy of the site control file just to read it.
    Set SCIComponentSet = connection.ExecQuery(query)

    ' The query returns only one instance.
    For Each SCIComponent In SCIComponentSet
        For Each vProperty In SCIComponent.PropLists
            If vProperty.PropertyListName = "Summary_Intervals" Then
                For i = 0 To UBound(vProperty.Values)
                    WScript.Echo vProperty.Values(i)
                Next
            End If
        Next
    Next
 End Sub
```

```c#
public void ShowSiteTallyIntervals(WqlConnectionManager connection, string siteCode)
{
    try
    {
        // Query for the site's site control file SMS_COMPONENT_STATUS_SUMMARIZER property lists.
        IResultObject query =
            connection.QueryProcessor.ExecuteQuery("SELECT PropLists FROM SMS_SCI_Component " +
            "WHERE ComponentName = 'SMS_COMPONENT_STATUS_SUMMARIZER' " +
            "AND SiteCode = '" + siteCode + "'");

        foreach (IResultObject r in query)
        {
            // Get the summary intervals and display them.
          if (r.EmbeddedPropertyLists.ContainsKey("Summary_Intervals"))
            {
                Console.WriteLine(r.EmbeddedPropertyLists["Summary_Intervals"]["PropertyListName"].StringValue);
                foreach (string value in r.EmbeddedPropertyLists["Summary_Intervals"]["Values"].StringArrayValue)
                {
                    Console.WriteLine(value);
                }
            }
            else
            {
                Console.WriteLine("Not found");
                return;
            }
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to tally intervals: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: [WqlConnectionManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/managed-sms-provider-fundamentals-in-configuration-manager#wqlconnectionmanager)  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals). |
| `siteCode` | - Managed: `String`  <br>- VBScript: `String` | A valid Configuration Manager site code. |

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

[About status messages](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-messages) [About Configuration Manager Tally Intervals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-tally-intervals) [About Configuration Manager Status Summarizers](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-summarizers)
