<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-connect-to-the-client-wmi-namespace -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Connect to the Configuration Manager Client WMI Namespace by Using System.Management

To connect to the Configuration Manager client Windows Management Instrumentation \(WMI\) provider, you create a `ManagementScope` object in the \\\\Client\\root\\ccm namespace.

You use the `ManagementScope` object to read and query WMI objects. For example, [How to Read a WMI Object Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-read-a-wmi-object-by-using-system.management).

### To connect to the Configuration Manager client WMI provider

1. In Visual Studio, create a new Visual C# Console Project.
2. Add a reference to the System.Management assembly.
3. In the C# source code, add a reference to the System.Management namespace with the following code.
4. `using System.Management;`
5. Create a new class and add the following connection example code.

## Example

The following C# code example creates and returns a `ManagementScope` object on the root\\ccm namespace.

For information about calling the sample code, see [How to Call a WMI Class Method by Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-call-a-wmi-class-method-by-using-system.management).

```c#

public ManagementScope Connect()  
{  
    try  
    {  
        return new ManagementScope(@"root\ccm");  
    }  
    catch (System.Management.ManagementException e)  
    {  
        Console.WriteLine("Failed to connect", e.Message);  
        throw;  
    }  
}  
```

## Compiling the Code

### Namespaces

System

System.Management

### Assembly

System.Management.dll

## Robust Programming

The exception that can be raised is [System.Management.ManagementException](https://learn.microsoft.com/en-us/dotnet/api/system.management.managementexception).

## See Also

[About Configuration Manager WMI Programming](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/about-configuration-manager-wmi-programming)  
[How to Call a WMI Class Method by Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-call-a-wmi-class-method-by-using-system.management)  
[How to Perform an Asynchronous Query by Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-perform-an-asynchronous-query-by-using-system.management)  
[How to Perform a Synchronous Query by Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-perform-a-synchronous-query-by-using-system.management)  
[How to Read a WMI Object by Using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-read-a-wmi-object-by-using-system.management)
