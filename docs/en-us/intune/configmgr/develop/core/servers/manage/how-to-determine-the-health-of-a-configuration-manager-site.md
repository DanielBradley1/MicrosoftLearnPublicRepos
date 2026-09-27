<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-determine-the-health-of-a-configuration-manager-site -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Determine the Health of a Configuration Manager Site

You can determine the overall health or status of a site, in Configuration Manager, by inspecting the `SMS_SummarizerSiteStatus` object `Status` property. The `Status` property has three possible values:

| Value | Description |
| --- | --- |
| 0 | The site is healthy. |
| 1 | The site has warning conditions. |
| 2 | The site has error conditions. |

`SMS_SummarizerSiteStatus` is an example of a Configuration Manager summarizer. For more information, see [SMS\_SummarizerSiteStatus server WMI class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_summarizersitestatus-server-wmi-class).

### To determine a site's health

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get the `SMS_SummarizerSiteStatus` object by using the Configuration Manager site code.
3. Inspect the `SMS_SummarizerSiteStatus` object `Status` property to determine the site status

## Example

The following example determines the health of the site code supplied in the parameter `siteCode`.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub ShowSiteHealth(connection, siteCode)

    Dim siteHealth
    Dim health

    On Error Resume Next

    ' Get the site status summarizer.
    Set siteHealth = connection.Get("SMS_SummarizerSiteStatus.SiteCode='" & siteCode & "'")
    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get site health"
        Exit Sub
    End If

    ' Display the site health.
    health="Health for site " + siteCode + " "

    Select Case siteHealth.Status
        Case 0
            heath = health + "is OK"
        Case 1
            health = health + "has warnings"
        Case 2
            health = health + "is critical"
        Case Else
            health = health + "is not known"
    End Select

    Wscript.Echo health
End Sub
```

```c#
public void ShowSiteHealth(WqlConnectionManager connection, string siteCode)
{
    try
    {
        IResultObject siteHealth = connection.GetInstance(@"SMS_SummarizerSiteStatus.SiteCode='" + siteCode + "'");

        Console.Write("Health for site {0}", siteCode);
        switch (siteHealth["Status"].IntegerValue)
        {
            case 0:
                Console.WriteLine("is OK");
                break;
            case 1:
                Console.WriteLine("has warnings");
                break;
            case 2:
                Console.WriteLine("is critical");
                break;
            default:
                Console.WriteLine("is not known");
                break;
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to show site status: " + e.Message);
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: [WqlConnectionManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/managed-sms-provider-fundamentals-in-configuration-manager#wqlconnectionmanager)  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals). |
| `siteCode` | - Managed: `String`  <br>- VBScript: `String` | A valid task Configuration Manager site code |

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

[About status messages](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-messages)
