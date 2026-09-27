<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-an-operating-system-deployment-task-sequence-action -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Add an Operating System Deployment Task Sequence Action

An operating system deployment task sequence action is added to a task sequence, in Configuration Manager, by creating an instance of an [SMS\_TaskSequence\_Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class) derived class and then adding it to the steps of the task sequence.

Note

Configuration Manager has a number of built-in actions that you can use. For example the command-line action class is [SMS\_TaskSequence\_RunCommandLineAction](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_runcommandlineaction-server-wmi-class). These classes derive from the [SMS\_TaskSequence\_Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class) class.

[SMS\_TaskSequenceAction](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class) derives from the [SMS\_TaskSequence\_Step](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class) class, which is the base class for both actions and groups. The task sequence stores its steps in an array of [SMS\_TaskSequence\_Step](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class), thus allowing actions and groups to be stored together.

### To add a task sequence action

1. Set up a connection to the SMS Provider. For more information see, [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Create a task sequence \([SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class)\) object. For more information, see [How to Create an Operating System Deployment Task Sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence).
3. Create an [SMS\_TaskSequenceAction](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class) derived class instance, for example, [SMS\_TaskSequence\_RunCommandLineAction](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_runcommandlineaction-server-wmi-class), for the action you want.
4. Populate the action as appropriate.
5. Add the action to the task sequences steps. This is stored the [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class)\) class Steps property.

## Example

The following example method creates a command-line action and adds it to the supplied task sequence.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub AddTaskSequenceActionCommandLine(connection, taskSequence, name, description)

    Dim steps
    Dim action

    Set action = connection.Get("SMS_TaskSequence_RunCommandLineAction").SpawnInstance_

    action.CommandLine = "cmd /c Echo Hello"
    action.Name=name
    action.Description=description
    action.Enabled=True
    action.ContinueOnError=False

      If IsNull(taskSequence.Steps) Then
        steps = Array(action)
        taskSequence.Steps=steps
    Else
        steps= Array(taskSequence.Steps)
        ReDim steps (UBound (taskSequence.Steps)+1)
        taskSequence.Steps(UBound(steps))=action
    End if

End Sub
```

```c#
public IResultObject AddTaskSequenceActionCommandLine(
    WqlConnectionManager connection,
    IResultObject taskSequence,
    string name,
    string description)
{
    try
    {
        // Create the new step.
        IResultObject ro;

        ro = connection.CreateEmbeddedObjectInstance("SMS_TaskSequence_RunCommandLineAction");
        ro["CommandLine"].StringValue = @"cmd /c Echo Hello";

        ro["Name"].StringValue = name;
        ro["Description"].StringValue = description;
        ro["Enabled"].BooleanValue = true;
        ro["ContinueOnError"].BooleanValue = false;

        // Add the step to the task sequence.
        List<IResultObject> array = taskSequence.GetArrayItems("Steps");

        array.Add(ro);

        taskSequence.SetArrayItems("Steps", array);

        return ro;
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to add action: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `taskSequence` | - Managed: `IResultObject`  <br>- VBScript: [SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject) | A valid task sequence. |
| `Name` | - Managed: `String`  <br>- VBScript: `String` | A name for the new action. |
| `Description` | - Managed: `String`  <br>- VBScript: `String` | A description for the action. |

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

[Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Add a Condition to an Operating System Deployment Task Sequence Step](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-condition-to-an-operating-system-deployment-task-sequence-step) [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [How to Create an Operating System Deployment Task Sequence Group](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-group) [How to Delete an Operating System Deployment Task Sequence Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-delete-an-operating-system-deployment-task-sequence-action) [Task sequence overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequences-overview)
