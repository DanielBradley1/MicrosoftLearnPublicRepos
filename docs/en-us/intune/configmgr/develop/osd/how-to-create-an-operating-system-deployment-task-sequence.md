<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Create an Operating System Deployment Task Sequence

You create a Configuration Manager operating system deployment task sequence by creating an instance of the [SMS\_TaskSequence](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence-server-wmi-class) class.

A task sequence contains one or more steps that are run sequentially on the client computer. For more information, see [Operating System Deployment Task Sequence Object Model](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequence-object-model).

The task sequence is then packaged in an [SMS\_TaskSequencePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequencepackage-server-wmi-class) and advertised to the client computer.

### To create a task sequence

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Create a task sequence `SMS_TaskSequence` object.
3. Add actions and, as required, add groups to the action. For more information, see [How to Add an Operating System Deployment Task Sequence Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-an-operating-system-deployment-task-sequence-action).
4. Associate the task sequence with a task sequence package. For more information, see [How to Create an Operating System Deployment Task Sequence Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package).
5. Advertise the task sequence to the client computer. For more information, see [How to Create an Advertisement](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-an-advertisement).

## Example

The following example method creates a task sequence that installs a software program. The example also creates a task sequence package by calling the example that is defined in [How to Create an Operating System Deployment Task Sequence Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub CreateInstallSoftwareTaskSequence(connection,name, description, packageID, programName)

    ' Create the task sequence.
    set taskSequence = connection.Get("SMS_TaskSequence").SpawnInstance_

    ' Create the action.
    set action = connection.Get("SMS_TaskSequence_InstallSoftwareAction").SpawnInstance_

    action.ProgramName=programName
    action.PackageID=packageID
    action.Name=name
    action.Enabled=true
    action.ContinueOnError=false

    ' Create an array to hold the action.
    actionSteps= array(action)
    ' Add the array to the task sequence.
    taskSequence.Steps=actionSteps

    wscript.echo taskSequence.Steps(0).Name
    call CreateTaskSequencePackage (connection, taskSequence)

 End Sub
```

```c#
public void CreateInstallSoftwareTaskSequence(
    WqlConnectionManager connection,
    string name,
    string packageId,
    string programName)
{
    try
    {
        // Create the task sequence.
        IResultObject taskSequence = connection.CreateInstance("SMS_TaskSequence");

        IResultObject ro = connection.CreateEmbeddedObjectInstance("SMS_TaskSequence_InstallSoftwareAction");
        ro["ProgramName"].StringValue = programName;
        ro["packageId"].StringValue = packageId;
        ro["Name"].StringValue = name;
        ro["Enabled"].BooleanValue = true;
        ro["ContinueOnError"].BooleanValue = false;

        // Add the step to the task sequence.
        List<IResultObject> array = taskSequence.GetArrayItems("Steps");

        array.Add(ro);

        taskSequence.SetArrayItems("Steps", array);

        // Create the task sequence package.
        this.CreateTaskSequencePackage(connection, taskSequence);
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
| `Connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `name` | - Managed: `String`  <br>- VBScript: `String` | The task sequence step name. |
| `description` | - VBScript: `String` | The task sequence step description. |
| `packageID` | - Managed: `String`  <br>- VBScript: `String` | The package identifier containing the software to be installed. Obtained from `SMS_Package.PackageID`. |
| `programName` | - Managed: `String`  <br>- VBScript: `String` | The name of the program to be installed. Obtained from `SMS_Program.ProgramName`. |

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

[Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview) [How to Connect to an SMS Provider in Configuration Manager by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code) [How to Connect to an SMS Provider in Configuration Manager by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) [Task sequence overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/operating-system-deployment-task-sequences-overview) [How to Create an Operating System Deployment Task Sequence Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package)
