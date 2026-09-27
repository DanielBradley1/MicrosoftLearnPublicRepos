<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-enumerate-the-available-operating-system-deployment-task-sequences -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Enumerate the Available Operating System Deployment Task Sequences

You enumerate the available operating system deployment task sequences, in Configuration Manager, by querying the available task sequence packages. Configuration Manager does not maintain instances of the [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) class for task sequences, but there is one instance of the [SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) class for each task sequence.

Note

Several properties are lazy and you must get the object instance before you can access the properties.

You can also access individual task sequence packages by using the [PackageID](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) key property. For an example, see [How to Read a Configuration Manager Object by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-object-by-using-managed-code). After you have the task sequence package, you must create an [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) object for the task sequence before you can change it. For more information, see [How to Read a Task Sequence From a Task Sequence Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-read-a-task-sequence-from-a-task-sequence-package).

### To enumerate the available task sequence packages

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Query the SMS Provider for the available instances of [SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class).
3. Display the required properties for each task sequence package returned by the query.

## Example

The following example method queries the SMS Provider for the available instance of [SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class). To retrieve the lazy properties, the example gets the entire object from the SMS Provider.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub EnumerateTaskSequencePackages(connection)

    Set taskSequencePackages= connection.ExecQuery("Select * from SMS_TaskSequencePackage")

    For Each package in taskSequencePackages
        WScript.Echo package.Name
        WScript.Echo package.Sequence
    Next
End Sub
```

```c#
public void EnumerateTaskSequencePackages(
    WqlConnectionManager connection)
{
    IResultObject taskSequencePackages = connection.QueryProcessor.ExecuteQuery("select * from SMS_TaskSequencePackage");

    foreach (IResultObject ro in taskSequencePackages)
    {
        ro.Get();

        // Get the lazy properties - Sequence property contains the Task sequence XML.
        Console.WriteLine(ro["Name"].StringValue);
        Console.WriteLine(ro["Sequence"].StringValue);

        Console.WriteLine();
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

## Compiling the Code

The C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/role-based-administration).

## See Also

[Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [How to Create an Operating System Deployment Task Sequence Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package) [How to Read a Task Sequence From a Task Sequence Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-read-a-task-sequence-from-a-task-sequence-package) [Task sequence overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequences-overview)
