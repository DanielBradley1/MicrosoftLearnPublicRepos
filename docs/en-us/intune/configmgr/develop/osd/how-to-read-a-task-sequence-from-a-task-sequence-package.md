<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-read-a-task-sequence-from-a-task-sequence-package -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Read a Task Sequence from a Task Sequence Package

You read a task sequence from a task sequence package, in Configuration Manager, by calling the [SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) class [GetSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getsequence-method-in-class-sms_tasksequencepackage) method. GetSequence returns an [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) object that you can change and then put back in the package by using the [SetSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage) method. For an example of using SetSequence, see [How to Create an Operating System Deployment Task Sequence Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package).

## To read a task sequence from a task sequence package

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Query the SMS Provider for the [SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) that you want to load the sequence from.
3. Call the [SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) class [GetSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getsequence-method-in-class-sms_tasksequencepackage) method to get the [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) object.
4. Make changes to the task sequence and put them back into the package by using [SetSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage).

### Example

The following example method returns the task sequence object \([SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class)\) from the supplied package.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Function ReadTaskSequence(connection, taskSequencePackage)
    ' Get the parameters object.
    Set packageClass = connection.Get("SMS_TaskSequencePackage")

    Set objInParam = packageClass.Methods_("GetSequence"). _
        inParameters.SpawnInstance_()

    ' Add the input parameters.
     objInParam.Properties_.Item("TaskSequencePackage") =  taskSequencePackage

    ' Get the sequence.
     Set objOutParams = connection.ExecMethod("SMS_TaskSequencePackage", "GetSequence", objInParam)
     Set ReadTaskSequence = objOutParams.TaskSequence
End Function
```

```c#
public IResultObject ReadTaskSequence(
    WqlConnectionManager connection,
    IResultObject taskSequencePackage)
{
    IResultObject taskSequence = null;
    try
    {
        Dictionary<string, object> parameters = new Dictionary<string, object>();
        parameters.Add("TaskSequencePackage", taskSequencePackage);

        IResultObject outParams = connection.ExecuteMethod("SMS_TaskSequencePackage", "GetSequence", parameters);
        taskSequence = outParams.GetSingleItem("TaskSequence");

        return taskSequence;
    }
    catch (Exception e)
    {
        Console.WriteLine("failed to hydrate: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

## Compiling the Code

This C# example requires:

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

[Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview)

[How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code)

[How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi)

[How to Create an Operating System Deployment Task Sequence Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package)

[Task sequence overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequences-overview)

[How to Enumerate the Available Operating System Deployment Task Sequences](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-enumerate-the-available-operating-system-deployment-task-sequences)
