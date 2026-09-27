<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Create an Operating System Deployment Task Sequence Package

You create an operating system deployment task sequence, in Configuration Manager, by creating an instance of the [SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) class. This class derives from the [SMS\_Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class) class and holds the task sequence. It is advertised to clients who can then run the task sequence. The task sequence is associated with the task sequence package by using the `SMS_TaskSequencePackage` class [SetSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/setsequence-method-in-class-sms_tasksequencepackage) method.

You can organize task sequence packages into categories by assigning a category to them with the [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) class *Category* property.

For more information about creating task sequences, see [How to Create a Task Sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence). For more information about task sequence packages, see the [Task Sequencing Object Model](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequence-object-model).

You advertise a task sequence package in the same way that you advertise a Configuration Manager package `SMS_Package`. For more information, see [How to Create an Advertisement](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-an-advertisement).

### To create a task sequence package

1. Set up a connection to the SMS Provider. For more information, see [About the SMS Provider in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code).
2. Create an instance of `SMS_TaskSequencePackage`.
3. Populate the task sequence package properties.
4. Call the `SMS_TaskSequencePackage` class `SetSequence` method to associate a task sequence \(`SMS_TaskSequence`\) with the task sequence package.

## Example

The following example method creates a task sequence package \(`SMS_TaskSequencePackage`\) and associates task sequence \(`SMS_TaskSequence`\) with it.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub CreateTaskSequencePackage (connection, taskSequence)

    Dim taskSequencePackage
    Dim packageClass
    Dim objInParams
    Dim objOutParams

    ' Create the new package object.
    Set taskSequencePackage = connection.Get("SMS_TaskSequencePackage").SpawnInstance_

    ' Populate the new package properties.
    taskSequencePackage.Name = "New task sequence package"
    taskSequencePackage.Description = "A new task sequence package description"

    ' Get the parameters object.
    Set packageClass = connection.Get("SMS_TaskSequencePackage")

    Set objInParams = packageClass.Methods_("SetSequence"). _
        inParameters.SpawnInstance_()

    ' Add the input parameters.
    objInParams.TaskSequence =  taskSequence
    objInParams.TaskSequencePackage = taskSequencePackage

    ' Add the sequence.
     Set objOutParams = connection.ExecMethod("SMS_TaskSequencePackage", "SetSequence", objInParams)

End Sub
```

```c#
public IResultObject CreateTaskSequencePackage(
    WqlConnectionManager connection,
    IResultObject taskSequence)
{
    try
    {
        Dictionary<string, object> inParams = new Dictionary<string, object>();

        // Create the new task sequence package.
        IResultObject taskSequencePackage = connection.CreateInstance("SMS_TaskSequencePackage");

        taskSequencePackage["Name"].StringValue = "New task sequence package";
        taskSequencePackage["Description"].StringValue = "A brand new task sequence package";
        taskSequencePackage["Category"].StringValue = "A custom category";

        // Note. Add other package properties as required.

        // Set up parameters that associate the task sequence with the package.
        inParams.Add("TaskSequence", taskSequence);
        inParams.Add("TaskSequencePackage", taskSequencePackage);

        // Associate the task sequence with the package. Note that a call to Put is not required.
        IResultObject result = connection.ExecuteMethod("SMS_TaskSequencePackage", "SetSequence", inParams);

        // The path to the new package.
        Console.WriteLine(result["SavedTaskSequencePackagePath"].StringValue);

        return taskSequencePackage;
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to create Task Sequence: " + e.Message);
        throw;
    }
}
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `taskSequence` | - Managed: `IResultObject`  <br>- VBScript: [SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject) | A valid task sequence `SMS_TaskSequence` |

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

[Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [How to Create a Task Sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence) [Task sequence overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequences-overview)
