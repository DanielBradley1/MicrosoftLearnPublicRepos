<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-perform-an-asynchronous-query-by-using-system.management -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Perform an Asynchronous Query by Using System.Management

To perform an asynchronous query on a Configuration Manager client Windows Instrumentation \(WMI\) namespace, create a `ManagementObjectSearcher` object that specifies a WQL query. You then create a `ManagementOperationObserver` that specifies an event handler for each query result and also for the end of the query.

The asynchronous query is run when the `ManagementObjectSearcher` object Get method is called with the `ManagementOperationObserver` object.

### To perform an asynchronous query

1. Set up a connection to the Configuration Manager client WMI namespace. For more information, see [How to Connect to the Configuration Manager Client WMI Namespace by Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-connect-to-the-client-wmi-namespace).
2. Create a `ManagementObjectSearcher` object.
3. Create a `ManagementOperationObserver` object.
4. Add an `ObjectReadyEventHandler` method the `ManagementOperationObserver` object.
5. Add a `CompletedEventHandler` method to the `ManagementOperationObserver`.
6. Call the `ManagementObjectSearcher` object Get method and supply the `ManagmentOperationObserver` object as a parameter.
7. Ensure your application still runs while the query is run.

## Example

The following C# code example asynchronously queries for components that are installed on a client.

For information about calling the sample code, see [How to Call a WMI Class Method by Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-call-a-wmi-class-method-by-using-system.management).

```c#

public void EnumerateInstancesAsync(ManagementScope scope)  
{  
    try  
    {  
        // Instantiate an object searcher with the query.  
        ManagementObjectSearcher searcher =  
            new ManagementObjectSearcher(scope, new  
            SelectQuery("CCM_InstalledComponent"));  

        // Create a results watcher object  
        // and handler for results and completion.  
        ManagementOperationObserver results = new  
            ManagementOperationObserver();  

        // Attach handler to events for results and completion.  
        results.ObjectReady += new  
            ObjectReadyEventHandler(this.NewObject);  
        results.Completed += new  
            CompletedEventHandler(this.Done);  

        Console.WriteLine("Installed Components");  
        Console.WriteLine("--------------------");  
        Console.WriteLine();  

        // Call the asynchronous overload of Get()  
        // to start the enumeration.  
        searcher.Get(results);  

        // Do something else while results  
        // arrive asynchronously.  
        while (!this.Completed)  
        {  
            System.Threading.Thread.Sleep(1000);  
        }  

        this.Reset();  
    }  
    catch (ManagementException e)  
    {  
        Console.WriteLine("Failed to run query: " + e.Message);  
        throw;  
    }  

}  

private bool isCompleted = false;  

private void NewObject(object sender,  
    ObjectReadyEventArgs obj)  
{  
    try  
    {  
        Console.WriteLine("Name: {0}, Version = {1}",  
            obj.NewObject["DisplayName"],  
            obj.NewObject["Version"]);  
    }  
    catch (ManagementException e)  
    {  
        Console.WriteLine("Error: " + e.Message);  
    }  

}  

private bool Completed  
{  
    get  
    {  
        return isCompleted;  
    }  
}  

private void Reset()  
{  
    isCompleted = false;  
}  

private void Done(object sender,  
         CompletedEventArgs obj)  
{  
    isCompleted = true;  
}  
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Scope` | `ManagementScope` | A valid `ManagementScope`. The path should be root\\ccm. |

## Compiling the Code

### Namespaces

System.

System.Management.

### Assembly

System.Management.

## Robust Programming

The exception that can be raised is [System.Management.ManagementException](https://learn.microsoft.com/en-us/dotnet/api/system.management.managementexception).

## See Also

[About Configuration Manager WMI Programming](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/about-configuration-manager-wmi-programming)  
[How to Call a WMI Class Method by Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-call-a-wmi-class-method-by-using-system.management)  
[How to Connect to the Configuration Manager Client WMI Namespace by Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-connect-to-the-client-wmi-namespace)  
[How to Perform a Synchronous Query by Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-perform-a-synchronous-query-by-using-system.management)  
[How to Read a WMI Object Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-read-a-wmi-object-by-using-system.management)
