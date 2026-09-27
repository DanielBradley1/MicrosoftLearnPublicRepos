<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/collections/how-to-get-the-properties-of-a-collection -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Get the Properties of a Collection

### To get the properties of a collection

1. Set up a connection to the SMS Provider.
2. Get the specific collection instance by using the collection ID provided.
3. Get the collection properties.

## Example

The following example method gets the properties of a collection.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub ReadCollectionProperties(connection, collectionID)    Dim collection    Dim statusText    Set collection = connection.Get("SMS_Collection.CollectionID='" & collectionID & "'")    WScript.Echo "Processing Collection - " & CStr(collection.CollectionID)    WScript.Echo "-- Name: " & collection.Name    WScript.Echo "-- Comment: " & collection.Comment    WScript.Echo "-- Members: " & CStr(collection.MemberCount)    statusText = "None"    Select Case collection.CurrentStatus    Case 1        statusText = "Ready"    Case 2        statusText = "Refreshing"    Case 5        statusText = "Awaiting Refresh"    End Select        WScript.Echo "-- Status: " & statusTextEnd Sub  
```

```c#
public void ReadCollectionProperties(WqlConnectionManager connection, string collectionID){    IResultObject collection = connection.GetInstance(string.Format("SMS_Collection.CollectionID='{0}'", collectionID));    string statusText = "None";    Console.WriteLine("Processing Collection - " + collectionID);    Console.WriteLine("-- Name: " + collection["Name"].StringValue);    Console.WriteLine("-- Comment: " + collection["Comment"].StringValue);    Console.WriteLine("-- Members: " + collection["MemberCount"].IntegerValue.ToString());    switch (collection["CurrentStatus"].IntegerValue)    {        case 1:            statusText = "Ready";            break;        case 2:            statusText = "Refreshing";            break;        case 5:            statusText = "Awaiting Refresh";            break;        default:            break;    }    Console.WriteLine("-- Status: " + statusText);}  
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `collectionID` | - Managed: `String`  <br>- VBScript: `String` | Unique auto-generated ID containing eight characters. For more information, see the CollectionID property of [SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class). |

## Compiling the Code

The C# example requires:

### Namespaces

System

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

mscorlib

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## See Also

[SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class)
