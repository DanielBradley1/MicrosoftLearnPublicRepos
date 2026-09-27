<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-list-the-maintenance-windows-and-properties-for-a-specific-collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to List the Maintenance Windows and Properties for a Specific Collection

The following example shows how to list the maintenance windows for a specific collection by using the [SMS\_CollectionSettings Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionsettings-server-wmi-class) class. Maintenance windows are created by using the [SMS\_ServiceWindow Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_servicewindow-server-wmi-class) class and then stored as embedded objects in [SMS\_CollectionSettings](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionsettings-server-wmi-class) instances, one per collection.

### To list the maintenance windows and properties for a collection

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get the existing collection settings instance by using the collection ID provided.
3. Enumerate the existing service window objects and properties.

Note

The example method includes additional steps, primarily to handle the overhead of dealing with the service window objects, which are stored as embedded objects in the collection settings instance.

## Example

The following example method lists the maintenance windows and properties for a collection.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs

Sub ListMaintenanceWindowsAndPropertiesForASpecificCollection(connection,         _
                                                              targetCollectionID)

    ' Build a query to get the specified collection.
     collectionSettingsQuery = "SMS_CollectionSettings.CollectionID='" & targetCollectionID & "'"

    ' Get the collection settings instance for the targetCollectionID.
    Set allCollectionSettings = connection.ExecQuery("Select * From SMS_CollectionSettings Where CollectionID = '" & targetCollectionID & "'")

    ' If a collection settings instance does not exist, output a message.
    If allCollectionSettings.Count = 0 Then
        Wscript.Echo "There are no maintenance windows for collection: " & targetCollectionID
    Else

    ' Get the specific collection settings instance.
    Set collectionSettingsInstance = connection.Get("SMS_CollectionSettings.CollectionID='" & targetCollectionID &"'" )

        ' Populate the local array list with the existing service window objects (from the target collection).
        tempMaintenanceWindowArray = collectionSettingsInstance.ServiceWindows

        ' Enumerate through the array list to access each maintenance window object.
        For Each maintenanceWindow in tempMaintenanceWindowArray

                Wscript.Echo "Maintenance Window Properties "
                Wscript.Echo "----------------------------- "
                Wscript.Echo "Name:              " & maintenanceWindow.Name
                Wscript.Echo "Description:       " & maintenanceWindow.Description
                Wscript.Echo "Service Window ID: " & maintenanceWindow.ServiceWindowID
                Wscript.Echo "Schedules:         " & maintenanceWindow.ServiceWindowSchedules
                Wscript.Echo "Is Enabled:        " & maintenanceWindow.IsEnabled
                Wscript.Echo "Type:              " & maintenanceWindow.ServiceWindowType
                Wscript.Echo " "

        Next

    End If

End Sub
```

```c#

public void ListMaintenanceWindowsAndPropertiesForASpecificCollection(WqlConnectionManager connection,
                                                                      string targetCollectionID)
{
    try
    {
        // Create an object to hold the collection settings instance (used to check whether a collection settings instance exists).
        IResultObject collectionSettingsInstance = null;

        // Get the collection settings instance for the targetCollectionID.
        IResultObject allCollectionSettings = connection.QueryProcessor.ExecuteQuery("Select * from SMS_CollectionSettings where CollectionID='" + targetCollectionID + "'");

        // Enumerate the allCollectionSettings collection (there should be just one item) and save the instance.
        foreach (IResultObject collectionSetting in allCollectionSettings)
        {
            collectionSettingsInstance = collectionSetting;
        }

        // If a collection settings instance, output message that there are no maintenance windows.
        if (collectionSettingsInstance == null)
        {
            Console.WriteLine("There are no maintenance windows for collection: " + targetCollectionID);
        }
        else
        {
            // Create a new array list to hold the service window objects.
            List<IResultObject> maintenanceWindowArray = new List<IResultObject>();

            // Establish connection to collection settings instance associated with the Collection ID.
            IResultObject collectionSettings = connection.GetInstance(@"SMS_CollectionSettings.CollectionID='" + targetCollectionID + "'");

            // Populate the array list with the existing service window objects (from the target collection).
            maintenanceWindowArray = collectionSettings.GetArrayItems("ServiceWindows");

            // Enumerate through the array list to access each maintenance window object and output specific properties for each object.
            foreach (IResultObject maintenanceWindow in maintenanceWindowArray)
            {
                Console.WriteLine("Maintenance Window Properties ");
                Console.WriteLine("----------------------------- ");
                Console.WriteLine("Name:              " + maintenanceWindow["Name"].StringValue);
                Console.WriteLine("Description:       " + maintenanceWindow["Description"].StringValue);
                Console.WriteLine("Service Window ID: " + maintenanceWindow["ServiceWindowID"].StringValue);
                Console.WriteLine("Schedules:         " + maintenanceWindow["ServiceWindowSchedules"].StringValue);
                Console.WriteLine("Is Enabled:        " + maintenanceWindow["IsEnabled"].BooleanValue);
                Console.WriteLine("Type:              " + maintenanceWindow["ServiceWindowType"].IntegerValue);
                Console.WriteLine(" ");
            };
        }
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
| `connection`  <br>  <br>`swebemServices` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `targetCollectionID` | - Managed: `String`  <br>- VBScript: `String` | The ID of the collection. |

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

## See also

[About maintenance windows](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/about-maintenance-windows) [Software distribution overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/software-distribution-overview) [About deployments](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/about-software-distribution-deployments) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Connect to a Configuration Manager Provider using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Connect to a Configuration Manager Provider Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [SMS\_CollectionSettings Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionsettings-server-wmi-class) [SMS\_ServiceWindow Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_servicewindow-server-wmi-class)
