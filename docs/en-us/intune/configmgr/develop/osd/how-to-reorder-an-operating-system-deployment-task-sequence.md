<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-reorder-an-operating-system-deployment-task-sequence -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Reorder an Operating System Deployment Task Sequence

In Configuration Manager, you can reorder the steps \(an action or a group\) in a task sequence or group by rearranging the step sequence in the [Steps](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) property [SMS\_TaskSequence\_Step](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class) array.

### To reorder a task sequence

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Obtain a valid task sequence \([SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class)\) or task sequence group \([SMS\_TaskSequence\_Group](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_group-server-wmi-class)\). For more information, see [How to Read a Task Sequence From a Task Sequence Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-read-a-task-sequence-from-a-task-sequence-package).
3. Within the `Steps` array property, move the [SMS\_TaskSequence\_Step](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_step-server-wmi-class) to its new location.
4. Update the task sequence or group.

## Example

The following example shows how to move a step up or down within a task sequence or group.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub MoveTaskSequenceStepDown(taskSequence, stepName)
   Dim index
   Dim osdStep
   Dim temp

    index=0

    ' If found, move the step down.
    for each osdStep in taskSequence.Steps
        If osdStep.Name=stepName Then
            If index < Ubound (TaskSequence.Steps) Then
                Set temp=osdStep
                taskSequence.Steps(index)=taskSequence.Steps(index+1)
                taskSequence.Steps(index+1)=temp
                Exit For
           End If
        End If

        index=index+1
    next
End Sub

Sub MoveTaskSequenceStepUp(taskSequence, stepName)
    Dim index
    Dim osdStep
    Dim temp

    index=0

    ' If found, move the step up.
    for Each osdStep In taskSequence.Steps
        If osdStep.Name=stepName Then
            If index >1 Then
                Set temp=osdStep
                taskSequence.Steps(index)=taskSequence.Steps(index-1)
                taskSequence.Steps(index-1)=temp
                Exit For
           End If
        End If

        index=index+1

    next
End Sub
```

```c#
public void MoveTaskSequenceStepDown(
    IResultObject taskSequence,
    string taskSequenceStepName)
{
    try
    {
        // Get the task sequence steps.
        List<IResultObject> steps = taskSequence.GetArrayItems("Steps"); // Array of SMS_TaskSequence_Steps.

        int index = 0;

        // Scan through the steps to find the step to move down.
        foreach (IResultObject ro in steps)
        {
            if (ro["Name"].StringValue == taskSequenceStepName)
            {
                // Move the step.
                if (index < steps.Count - 1) // Not at end, so we can flip.
                {
                    steps.Insert(index + 2, steps[index]);
                    steps.Remove(steps[index]);
                    taskSequence.SetArrayItems("Steps", steps);
                    break;
                }
            }

            index++;
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed To enumerate task sequence items: " + e.Message);
        throw;
    }
}

public void MoveTaskSequenceStepUp(
    IResultObject taskSequence,
    string taskSequenceStepName)
{
    try
    {
        // Get the task sequence steps.
        List<IResultObject> steps = taskSequence.GetArrayItems("Steps"); // Array of SMS_TaskSequence_Steps.

        int index = 0;

        foreach (IResultObject ro in steps)
        {
            if (ro["Name"].StringValue == taskSequenceStepName)
            {
                if (index > 0) // Not the first step, so you can move it up.
                {
                    steps.Insert(index + 1, steps[index - 1]);
                    steps.Remove(steps[index - 1]);
                    taskSequence.SetArrayItems("Steps", steps);
                    break;
                }
            }
            index++;
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed To enumerate task sequence items: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `taskSequence` | - Managed: `IResultObject`  <br>- VBScript: [SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject) | A valid task sequence or task sequence group |
| `taskSequenceStepName`  <br>  <br>`stepName` | - Managed: `String`  <br>- VBScript: `String` | The name of the task sequence step to move. |

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

[Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Add an Operating System Deployment Task Sequence Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-an-operating-system-deployment-task-sequence-action) [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [Task sequence overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequences-overview)
