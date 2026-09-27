<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/inventory/how-to-reset-the-software-inventory-cache -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Reset the Software Inventory Cache

In Configuration Manager, you reset the software inventory cache by connecting to the inventory agent namespace and deleting the inventory action status instance for software inventory.

### To reset the software inventory cache

1. Connect to the inventory agent namespace \(root\\ccm\\invagt\).
2. Delete the inventory action status instance for software inventory \({00000000-0000-0000-0000-000000000002}\).

## Example

The following example method shows how to reset the software inventory cache by connecting to the inventory agent namespace and deleting the inventory action status instance for software inventory.

For information about calling the sample code, see [How to Call a Configuration Manager Object Class Method by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-wmi)

```vbs

Sub ResetSoftwareInventoryCache()  

    ' Get a connection to the "root\ccm\invagt" namespace.  
    Dim locator  
    Set locator = CreateObject("WbemScripting.SWbemLocator")  
    Dim services  
    Set services = locator.ConnectServer( , "root\ccm\invagt")  

    ' Delete the specified InventoryActionStatus instance.  
    services.Delete "InventoryActionStatus.InventoryActionID='{00000000-0000-0000-0000-000000000002}'"        

    ' Display message.  
    wscript.echo "Reset Software Inventory cache."  

End Sub  
```

```c#

public void ResetSoftwareInventoryCache()  
{  
    try  
    {  
        // Define the scope (namespace).  
        ManagementScope inventoryAgentScope = new ManagementScope(@"root\ccm\invagt");  

        // Load the class that you want to work with.  
        ManagementClass inventoryClass = new ManagementClass(inventoryAgentScope.Path.Path, "InventoryActionStatus", null);  

        // Query the class for the InventoryActionID object (create query, create searcher object, execute query).  
        ObjectQuery query = new ObjectQuery("SELECT * FROM InventoryActionStatus WHERE InventoryActionID = '{00000000-0000-0000-0000-000000000002}'");  
        ManagementObjectSearcher searcher = new ManagementObjectSearcher(inventoryAgentScope, query);  
        ManagementObjectCollection queryResults = searcher.Get();  

        // Enumerate the collection to get to the result (there should only be one item returned from the query).  
        foreach (ManagementObject result in queryResults)  
        {  
            // Display message and delete the object.  
            Console.WriteLine("Resetting Software Inventory cache.");  
            result.Delete();  
        }  
    }  

    catch (System.Management.ManagementException ex)  
    {  
        Console.WriteLine("Failed to run action. Error: " + ex.Message);  
        throw;  
    }  
}  
```

## Compiling the Code

This C# example requires:

### Namespaces

System.Management

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/role-based-administration).

## See Also

[Configuration Manager Software Development Kit](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/misc/system-center-configuration-manager-sdk)  
[About Configuration Manager Inventory](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/inventory/about-configuration-manager-inventory)
