<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-query-by-using-managed-code -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Perform an Asynchronous Configuration Manager Query by Using Managed Code

In Configuration Manager, to perform an asynchronous query by using the managed SMS Provider, you use the [ProcessQuery](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc146295\(v=msdn.10\)) method.

The first parameter of the [ProcessQuery](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc146295\(v=msdn.10\)) method is an instance of the [SmsBackgroundWorker](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147429\(v=msdn.10\)) class that provides two event handlers:

- [QueryProcessObjectReady](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc143780\(v=msdn.10\)). This event handler is called for each object returned by the query. The event handler provides an IResultObject object that represents the object.
- [QueryProcessCompleted](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc143778\(v=msdn.10\)). This event handler is called when the query is completed. It also provides information about any errors that occur. For more information, see For information about error handling, see [How to Handle Configuration Manager Asynchronous Errors by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-managed-code).

  The second parameter to of the [ProcessQuery](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc146295\(v=msdn.10\)) method is the WQL statement for the query.

### To perform an asynchronous query

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Create the **SmsBackgroundWorker** object and populate the [QueryProcessorObjectReady](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc143780\(v=msdn.10\)) and [QueryProcessorCompleted](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc143778\(v=msdn.10\)) properties with the callback method names.
3. From the **WqlConnectionManager** object you obtain in step one, call the **QueryProcessor** object [ProcessQuery](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc146295\(v=msdn.10\)) method to start the asynchronous query.

## Example

The following example queries for all available SMS\_Collection objects, and in the event handler, the example writes several of the collection properties to the Configuration Manager console.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```
public void QueryCollections(WqlConnectionManager connection)
{
    try
    {
        // Set up the query.
        SmsBackgroundWorker bw1 = new SmsBackgroundWorker();
        bw1.QueryProcessorObjectReady += new EventHandler<QueryProcessorObjectEventArgs>(bw1_QueryProcessorObjectReady);
        bw1.QueryProcessorCompleted += new EventHandler<RunWorkerCompletedEventArgs>(bw1_QueryProcessorCompleted);

        // Query for all collections.
        connection.QueryProcessor.ProcessQuery(bw1, "select * from SMS_Collection");

        // Pause while query runs.
        Console.ReadLine();
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to start asynchronous query: ", ex.Message);
    }
}

void bw1_QueryProcessorObjectReady(object sender, QueryProcessorObjectEventArgs e)
{
    try
    {
        // Get the collection.
        IResultObject collection = (IResultObject)e.ResultObject;

        //Display properties.
        Console.WriteLine(collection["CollectionID"].StringValue);
        Console.WriteLine(collection["Name"].StringValue);
        Console.WriteLine();
        collection.Dispose();
    }
    catch (SmsQueryException eX)
    {
        Console.WriteLine("Query Error: " + eX.Message);
    }
}

void bw1_QueryProcessorCompleted(object sender, RunWorkerCompletedEventArgs e)
{
    Console.WriteLine("Done...");
}
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |

## Compiling the Code

### Namespaces

System

System.Collections.Generic

System.ComponentModel

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

The Configuration Manager exceptions that can be raised are [SmsConnectionException](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147431\(v=msdn.10\)) and [SmsQueryException](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147436\(v=msdn.10\)). These can be caught together with [SmsException](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147433\(v=msdn.10\)).

## See Also

[Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [Configuration Manager Lazy Properties](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-lazy-properties) [How to Call a Configuration Manager Object Class Method by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-call-a-configuration-manager-object-class-method-by-using-managed-code) [How to Connect to a Configuration Manager Provider using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Create a Configuration Manager Object by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-object-by-using-managed-code) [How to Modify a Configuration Manager Object by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-modify-a-configuration-manager-object-by-using-managed-code) [How to Perform a Synchronous Configuration Manager Query by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code) [How to Read a Configuration Manager Object by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-managed-code) [How to Read Lazy Properties by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-lazy-properties-by-using-managed-code) [How to Perform a Synchronous Configuration Manager Query Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code) [Configuration Manager Extended WMI Query Language](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/extended-wmi-query-language) [Configuration Manager Result Sets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/result-sets) [Configuration Manager Special Queries](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/special-queries) [About queries](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-queries)
