<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-configure-software-updates-to-override-maintenance-windows -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Configure Software Updates to Override Maintenance Windows

You configure software updates to override maintenance windows, in Configuration Manager, by updating the `OverrideServiceWindows` property of an assignment \(deployment\).

### To configure software updates to override maintenance windows

1. Set up a connection to the SMS Provider.
2. Load the specific assignment \(deployment\) to modify using the `SMS_UpdatesAssignment` class.
3. Set the `OverrideServiceWindows` value to `true`.
4. Save the assignment \(deployment\) and properties.

## Example

The following example method shows how to configure software updates to override maintenance windows by using the `SMS_UpdatesAssignment` class and class properties.

Note

This task only applies to mandatory deployments.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs

Sub ConfigureSoftwareUpdatestoOverrideMaintenanceWindow(connection, existingAssignmentID)

    ' Get the specific SMS_UpdatesAssignment instance to modify.
    Set assignmentToModify = connection.Get("SMS_UpdatesAssignment.AssignmentID=" & existingAssignmentID & "")

    ' Set the new property value.
    assignmentToModify.OverrideServiceWindows = true

    ' Save the assignment.
    assignmentToModify.Put_

    ' Output the new property values.
    Wscript.Echo " "
    Wscript.Echo "Set assignment " & existingAssignmentID & " to override service windows."

End Sub
```

```c#

public void ConfigureSoftwareUpdatestoOverrideMaintenanceWindow(WqlConnectionManager connection, int existingAssignmentID)
{
    try
    {
        // Get the specific SMS_UpdatesAssignment instance to change.
        IResultObject updatesAssignmentToChange = connection.GetInstance(@"SMS_UpdatesAssignment.AssignmentID=" + existingAssignmentID);

        // Set OverrideServiceWindows property.
        updatesAssignmentToChange["OverrideServiceWindows"].BooleanValue = true;

        // Save property changes.
        updatesAssignmentToChange.Put();

        // Output success message.
        Console.WriteLine("Set assignment " + existingAssignmentID + " to override service windows.");
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to .... Error: " + ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingAssignmentID` | - Managed: `Integer`  <br>- VBScript: `Integer` | An existing Assignment ID to modify. |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/role-based-administration).

## See also

[SMS\_UpdatesAssignment](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_updatesassignment-server-wmi-class)
