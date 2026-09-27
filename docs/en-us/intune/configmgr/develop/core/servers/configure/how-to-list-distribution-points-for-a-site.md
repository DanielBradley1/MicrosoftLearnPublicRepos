<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-list-distribution-points-for-a-site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to List Distribution Points for a Site

The following example shows how to assign a distribution point to a package by using the [SMS\_DistributionPoint Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpoint-server-wmi-class) class and class properties in Configuration Manager.

You only need to assign a distribution point to a package if the package contains source files. The package is not advertised until the program source files have been propagated to a distribution point share. You can use the default distribution point share, or you can specify a share to use. You can also specify more than one distribution point to use to distribute your package source files, although the following example does not demonstrate that.

Note

To identify branch distribution points, check the [IsPeerDP](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpoint-server-wmi-class) property of the specific [SMS\_DistributionPoint](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpoint-server-wmi-class) class instance. If the IsPeerDP property is true, then the distribution point is a branch distribution point.

### To list distribution points for a site

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Run a query, which populates a variable with a collection of distribution point objects.
3. Enumerate through the collection of and list the distribution points returned by the query.

## Example

The following example method lists distribution points for a site.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs

Sub ListDistributionPointsForSite(connection, siteCode)

    ' This query selects all distribution points for a site based on the provided site code.
    Query = "SELECT * FROM SMS_SystemResourceList WHERE RoleName='SMS Distribution Point' AND SiteCode='" & siteCode & "'"

    ' Run query, which populates listOfResources with a collection of objects.
    Set ListOfResources = connection.ExecQuery(query, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    ' Output header for list of distribution points.
    Wscript.Echo "List of distribution points for site: " & siteCode
    Wscript.Echo "--------------------------------------------"

    ' Enumerate through the collection of objects returned by the query.
    For Each resource In listOfResources
        ' Output the server name for each distribution point.
        Wscript.Echo resource.ServerName
    Next

End Sub
```

```c#
public void ListDistributionPointsForSite(WqlConnectionManager connection, string siteCode)
{
    try
    {
        // This query selects all distribution points for a site based on the provided site code.
        string query = "SELECT * FROM SMS_SystemResourceList WHERE RoleName='SMS Distribution Point' AND SiteCode='" + siteCode + "'";

        // Run query, which populates 'listOfResources' with a collection of objects.
        IResultObject listOfResources = connection.QueryProcessor.ExecuteQuery(query);

        // Output header for list of distribution points.
        Console.WriteLine("List of distribution points for site: " + siteCode);
        Console.WriteLine("--------------------------------------------");

        // Enumerate through the collection of objects returned by the query.
        foreach (IResultObject resource in listOfResources)
        {
            // Output the server name for each distribution point.
            Console.WriteLine(resource["ServerName"].StringValue);
        }
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to list distribution points. Error: " + ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection`  <br>  <br>`swebemServices` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `siteCode` | - Managed: `String`  <br>- VBScript: `String` | The site code for the site that supports the distribution points. |

## Compiling the Code

The C# example requires:

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

[Software distribution overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/software-distribution-overview) [About the Configuration Manager Site Control File](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file) [How to Read and Write to the Configuration Manager Site Control File by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-managed-code) [How to Read and Write to the Configuration Manager Site Control File by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-wmi) [SMS\_SCI\_Component Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_sci_component-server-wmi-class) [SMS\_DistributionPoint Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpoint-server-wmi-class)
