<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-step-to-an-operating-system-deployment-group -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Add a Step to an Operating System Deployment Group

You add a step \(an action or a group\) to an operating system deployment task sequence group, in Configuration Manager, by adding the step to the `SMS_TaskSequenceGroup.Steps` array property.

### To add a step to a task sequence group

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get the [SMS\_TaskSequenceGroup](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_group-server-wmi-class) object that you want to add the step to. For more information, see [How to Create an Operating System Deployment Task Sequence Group](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-group).
3. Create the task sequence step. For an example of creating an action step, see [How to Add an Operating System Deployment Task Sequence Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-an-operating-system-deployment-task-sequence-action).
4. Add the step to the `SMS_TaskSequenceGroup.Steps` array property.
5. Reorder the step within the array property as necessary. For more information, see [How to Re-order an Operating System Deployment Task Sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-reorder-an-operating-system-deployment-task-sequence)

## Example

The following example method adds a command-line action to a task sequence group.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub AddStepToGroup(taskSequenceStep, group)

    Dim steps

    ' If needed, create a new steps array.
    If IsNull(group.Steps) Then
        steps = Array(taskSequenceStep)
        group.Steps=steps
    Else
        ' Resize the existing steps and add step.
        steps= Array(group.Steps)
        ReDim steps (UBound (group.Steps)+1)
        group.Steps(UBound(steps))=taskSequenceStep
    End if

End Sub
```

```c#
public void AddStepToGroup(
    WqlConnectionManager connection,
    IResultObject taskSequence,
    string groupName)
{
    try
    {
        // Get the group.
        List<IResultObject> steps = taskSequence.GetArrayItems("Steps"); // Array of SMS_TaskSequence_Steps.

        foreach (IResultObject ro in steps)
        {
            if (ro["Name"].StringValue == groupName && ro["__CLASS"].StringValue == "SMS_TaskSequence_Group")
            {
                IResultObject action = connection.CreateEmbeddedObjectInstance("SMS_TaskSequence_RunCommandLineAction");
                action["CommandLine"].StringValue = @"C:\donowtingroup.bat";
                action["Name"].StringValue = "Action in group " + groupName;
                action["Description"].StringValue = "Action in a group";
                action["Enabled"].BooleanValue = true;
                action["ContinueOnError"].BooleanValue = false;

                // Add the step to the task sequence.
                List<IResultObject> array = ro.GetArrayItems("Steps");

                array.Add(action);

                ro.SetArrayItems("Steps", array);
                taskSequence.SetArrayItems("Steps", steps);
                break;
            }
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to create Task Sequence: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `taskSequence`  <br>  <br>`taskSequenceStep` | - Managed: `IResultObject`  <br>- VBScript: [SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject) | - A valid task sequence \([SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class)\) that contains the group. |
| `groupName`  <br>  <br>`group` | - Managed: `String`  <br>- VBScript: `String` | The name of the group that the command-line action is added to. This is obtained from the `SMS_TaskSequenceGroup.Name` property. |

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

[Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [How to Move a Step to a Different Operating System Deployment Task Sequence Group](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-move-a-step-to-a-different-task-sequence-group) [How to Create an Operating System Deployment Task Sequence Group](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-group) [How to Remove a Step From an Operating System Deployment Group](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-remove-a-step-from-an-operating-system-deployment-group) [Task sequence overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequences-overview)
