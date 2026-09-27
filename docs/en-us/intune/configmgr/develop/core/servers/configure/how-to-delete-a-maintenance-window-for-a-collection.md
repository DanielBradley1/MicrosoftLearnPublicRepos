<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-delete-a-maintenance-window-for-a-collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Delete a Maintenance Window for a Collection

You can delete maintenance window, in Configuration Manager, by using the [SMS\_CollectionSettings Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionsettings-server-wmi-class) and [SMS\_ServiceWindow Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_servicewindow-server-wmi-class) classes and properties.

### To delete a maintenance window for a collection

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get an existing collection settings instance by using the collection ID provided.
3. Get the existing service window object by using the maintenance window ID provided.
4. Delete the existing maintenance window.
5. Save the collection settings instance and properties.

Note

The example method includes additional steps, primarily to handle the overhead of dealing with the service window objects, which are stored as embedded objects in the collection settings instance.

## Example

The following example method deletes a specific maintenance window instance for a collection.

Important

This assumes that the collection instance can modified. This might not be the case at child sites, where the collections are owned by the parent site or sites.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```c#
public void DeleteMaintenanceWindowfromCollection(WqlConnectionManager connection,
                                                  string targetCollectionID,
                                                  string serviceWindowID)
{
    try
    {
        // Create a new array list to hold the service window objects.
        List<IResultObject> tempMaintenanceWindowArray = new List<IResultObject>();

        // Establish connection to collection settings instance associated with the target collection ID.
        IResultObject collectionSettings = connection.GetInstance(@"SMS_CollectionSettings.CollectionID='" + targetCollectionID + "'");

        // Populate the array list with the existing service window objects (from the target collection).
        tempMaintenanceWindowArray = collectionSettings.GetArrayItems("ServiceWindows");

        // Enumerate through the array list to access each maintenance window object.
        foreach (IResultObject maintenanceWindow in tempMaintenanceWindowArray)
        {
            // If the maintenance window ID matches the one passed in to the function, delete the maintenance window.
            if (maintenanceWindow["ServiceWindowID"].StringValue == serviceWindowID)
            {
                tempMaintenanceWindowArray.Remove(maintenanceWindow);
                Console.WriteLine("Deleted:");
                Console.WriteLine("Maintenance Window Name: " + maintenanceWindow["Name"].StringValue);
                Console.WriteLine("Maintenance Windows Service Window ID: " + maintenanceWindow["ServiceWindowID"].StringValue);
                break;
            }
        }

        // Replace the existing service window objects from the target collection with the temporary array that includes the new maintenance window.
        collectionSettings.SetArrayItems("ServiceWindows", tempMaintenanceWindowArray);

        // Save the new values in the collection settings instance associated with the Collection ID.
        collectionSettings.Put();
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
| `connection` | - Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `targetCollectionID` | - Managed: `String` | The ID of the collection. |
| `serviceWindowID` | - Managed: `String` | The ID of the maintenance window to delete. |

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

[About maintenance windows](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/about-maintenance-windows) [Software distribution overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/software-distribution-overview) [About deployments](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/about-software-distribution-deployments) [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Connect to a Configuration Manager Provider using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Connect to a Configuration Manager Provider Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [SMS\_CollectionSettings Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionsettings-server-wmi-class) [SMS\_ServiceWindow Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_servicewindow-server-wmi-class)
