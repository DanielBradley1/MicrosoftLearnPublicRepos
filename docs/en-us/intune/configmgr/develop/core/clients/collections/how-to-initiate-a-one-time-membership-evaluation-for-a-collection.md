<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/collections/how-to-initiate-a-one-time-membership-evaluation-for-a-collection -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Initiate a One-time Membership Evaluation for a Collection

### To Initiate a One-time Membership Evaluation

1. Set up a connection to the SMS Provider.
2. Get the specific collection instance by using the collection ID provided.
3. Refresh the collection membership using the [RequestRefresh](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/requestrefresh-method-in-class-sms_collection) method in the [SMS\_Collection](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) class.

## Example

The following example method refreshes the collection membership for a specific collection.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub RefreshCollection(connection, collectionID)    Dim collection    Set collection = connection.Get("SMS_Collection.CollectionID='" & collectionID & "'")    Call collection.RequestRefresh()End Sub  
```

```c#
public void RefreshCollection(WqlConnectionManager connection, string collectionID){    IResultObject collection = connection.GetInstance(string.Format("SMS_Collection.CollectionID='{0}'", collectionID));    collection.ExecuteMethod("RequestRefresh", null);}  
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
