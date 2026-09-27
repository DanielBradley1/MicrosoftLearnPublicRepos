<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-read-user-defined-status-messages -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Read User-Defined Status Messages

In Configuration Manager, you can read user-defined status messages, on the site server, by querying the SMS Provider.

### To read a user-defined status messages

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Query the provider for the SMS`_StatusMessage` instances you want. As part of the query get the insertion string values from `SMS_SMS_StatMsgInStrings` and the attribute value from `SMS_StatMsgAttributes`.

## Example

The following example reads error message status messages for the sample created in [How to Report User-Defined Status Messages Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-report-user-defined-status-messages). Make sure the `MyPackageID` and `MyApplication` values in the query match in both samples.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub ReadErrorStatusMesage(connection)

    Dim queryWQL
    Dim message
    Dim messageSet
    Dim statusMessage
    Dim insertionString
    Dim attributes

    queryWQL = "SELECT b.Component, b.MachineName, b.MessageType, b.MessageID, " & _
            "       c.InsStrValue, d.AttributeValue " & _
            "FROM SMS_StatusMessage b " & _
            "     JOIN SMS_StatMsgInsStrings c ON b.RecordID = c.RecordID " & _
            "     JOIN SMS_StatMsgAttributes d ON c.RecordID = d.RecordID " & _
            "WHERE b.Component = 'MyApplication' " & _
            "AND   d.AttributeID = 400 " & _
            "AND   d.AttributeValue = 'MyPackageID' "

    Set messageSet = connection.ExecQuery(queryWQL)

    For Each message in messageSet

        ' Get the message objects.
        statusMessage = message.Properties_.Item("b")
        insertionString = message.Properties_.Item("c")
        attributes = message.Properties_.Item("d")

        ' Display the message details.
        WScript.Echo "Message: " + insertionString.Properties_.Item("insstrvalue")
        WScript.Echo "Component: " + statusMessage.Properties_.Item("Component")
        WScript.Echo "Computer: " + statusMessage.Properties_.Item("MachineName")
        WScript.Echo "MessageID: " + Cstr(statusMessage.Properties_.Item("MessageID"))
        WScript.Echo attributes.Properties_.Item("attributevalue")
        WScript.Echo

    Next

 End Sub
```

```c#
public void ReadErrorStatusMessage(WqlConnectionManager connection)
{
    try
    {
        string queryWQL = "SELECT b.Component, b.MachineName, " +
                "       b.MessageType, b.MessageID, " +
                "       c.insstrvalue, d.attributevalue " +
                "FROM SMS_StatusMessage b " +
                "     JOIN SMS_StatMsgInsStrings c ON b.RecordID = c.RecordID " +
                "     JOIN SMS_StatMsgAttributes d ON c.RecordID = d.RecordID " +
                "WHERE b.Component = \"MyApplication\" " +
                "AND   d.AttributeID = 400 " +
                "AND   d.AttributeValue = \"MyPackageID\" ";

        IResultObject query = connection.QueryProcessor.ExecuteQuery(queryWQL);
        foreach (IResultObject o in query)
        {

            ManagementBaseObject  statusMessage = (ManagementBaseObject)o["b"].ObjectValue;
            ManagementBaseObject insertionString = (ManagementBaseObject)o["c"].ObjectValue;
            ManagementBaseObject attributes = (ManagementBaseObject)o["d"].ObjectValue;

            Console.WriteLine("Message: " + insertionString["insstrvalue"]);
            Console.WriteLine("Component: " + statusMessage["Component"]);
            Console.WriteLine("Computer: " + statusMessage["MachineName"]);
            Console.WriteLine("MessageID: " + statusMessage["MessageID"]);
            Console.WriteLine(attributes["attributevalue"]);
            Console.WriteLine();
        }
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to read status message: ", ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: [WqlConnectionManager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/managed-sms-provider-fundamentals-in-configuration-manager#wqlconnectionmanager)  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals). |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

System.Management

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

System.Management

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/role-based-administration).

## See Also

[About Configuration Manager Status Messages](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-messages) [How to Report User-Defined Status Messages](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-report-user-defined-status-messages) [SMS\_StatusMessage Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class) [How To Delete Status Messages](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/how-to-delete-status-messages)
