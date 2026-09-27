<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-set-an-operating-system-deployment-task-sequence-variable -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Set an Operating System Deployment Task Sequence Variable

In Configuration Manager, you create an operating system deployment task sequence variable by creating an instance of the [SMS\_TaskSequence\_SetVariableAction](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_setvariableaction-server-wmi-class) class, adding to a task sequence. You can also create task sequence variables while the task sequence is running on the client. For more information, see [How to Use Task Sequence Variables in a Running Configuration Manager Task Sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence).

A task sequence variable is a name/value pair that you can access by task sequence steps. You can also create computer and collection-specific variables. For more information, see [How to Create a Collection Variable in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-collection-variable) and [How to Create a Computer Variable in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-computer-variable).

Note

Variables that are set with the [SMS\_TaskSequence\_SetVariableAction](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_setvariableaction-server-wmi-class) class override variables that are set elsewhere. For example, if a collection variable and a SMS\_TaskSequence\_SetVariableAction have the same name, the value of the SMS\_TaskSequence\_SetVariableAction variable takes precedence.

### To set a task sequence variable

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get a task sequence to add the task sequence variable to. For more information, see [How to Create an Operating System Deployment Task Sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence).
3. Create an instance of [SMS\_TaskSequence\_SetVariableAction](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_setvariableaction-server-wmi-class).
4. Set the VariableName and VariableValue properties for the variable that you are adding.
5. Add the SMS\_TaskSequence\_SetVariableAction object to the task sequence.

## Example

The following example method sets a task sequence variable name and value.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub AddTaskSequenceVariable(connection, taskSequence, variableName, variableValue)

    Dim variable
    Dim steps

    Set variable = connection.Get("SMS_TaskSequence_SetVariableAction").SpawnInstance_

    variable.Name="MyTaskSequenceVariable"
    variable.Description = "A task sequence variable"
    variable.Enabled=True
    variable.ContinueOnError=False
    variable.VariableName=variableName
    variable.VariableValue=variableValue

    steps= Array(taskSequence.Steps)

    ReDim steps (UBound (taskSequence.Steps)+1)

    taskSequence.Steps(UBound(steps))=variable

End Sub
```

```c#
public void AddTaskSequenceVariable(
    WqlConnectionManager connection,
    IResultObject taskSequence,
    string variableName,
    string variableValue)
{
    try
    {
        // Create the task sequence variable object.
        IResultObject variable = connection.CreateEmbeddedObjectInstance("SMS_TaskSequence_SetVariableAction");

        // Populate the properties.
        variable["Name"].StringValue = "MyTaskSequenceVariable";
        variable["ContinueOnError"].BooleanValue = false;
        variable["Description"].StringValue = "A task sequence variable set with SMS_TaskSequence_SetVariableAction";
        variable["Enabled"].BooleanValue = true;
        variable["VariableName"].StringValue = variableName;
        variable["VariableValue"].StringValue = variableValue;

        // Add the step to the task sequence.
        List<IResultObject> array = taskSequence.GetArrayItems("Steps");

        array.Add(variable);
        taskSequence.SetArrayItems("Steps", array);
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to set task sequence variable: " + e.Message);
        throw;
    }
}
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | - A valid connection to the SMS Provider. |
| `taskSequence` | - Managed: `WqlConnectionManager`  <br>- VBScript: `SWbemServices` | - The task sequence the variable is added to. |
| `variableName` | - Managed: `String`  <br>- VBScript: `String` | The name of the variable. |
| `variableValue` | - Managed: `String`  <br>- VBScript: `String` | The value for the variable. |

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

[Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [Task sequence overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequences-overview) [How to Use Task Sequence Variables in a Running Configuration Manager Task Sequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence) [How to Read a Task Sequence from a Task Sequence Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-read-a-task-sequence-from-a-task-sequence-package)
