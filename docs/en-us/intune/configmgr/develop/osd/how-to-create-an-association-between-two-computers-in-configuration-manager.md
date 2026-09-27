<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-association-between-two-computers-in-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Create an Association Between Two Computers in Configuration Manager

You create an association between a reference and destination computer, in Configuration Manager, by calling the [AddAssociation Method in Class SMS\_StateMigration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/addassociation-method-in-class-sms_statemigration).

Note

You call the [DeleteAssociation Method in Class SMS\_StateMigration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/deleteassociation-method-in-class-sms_statemigration) to delete an association.

### To create an association between two computers

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Call the [AddAssociation Method in Class SMS\_StateMigration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/addassociation-method-in-class-sms_statemigration).

## Example

The following example method adds an association between a source and reference computer.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub AssociateComputer(connection, referenceComputerResourceId, destinationComputerResourceId)

    Dim stateMigrationClass
    Dim inParams
    Dim outParams

    ' Get the state migration class.
    Set stateMigrationClass = connection.Get("SMS_StateMigration")

    ' Set up the parameters.
    Set inParams = _
      stateMigrationClass.Methods_("AddAssociation").InParameters.SpawnInstance_
    inParams.SourceClientResourceID = referenceComputerResourceId
    inParams.RestoreClientResourceID = destinationComputerResourceId

    ' Call the method.
    Set outParams = _
      connection.ExecMethod( "SMS_StateMigration", "AddAssociation", inParams)

   End Sub
```

```c#
public void AssociateComputer(
    WqlConnectionManager connection,
    int referenceComputerResourceId,
    int destinationComputerResourceId)
{
    try
    {
        // Set up the reference and destination computer in parameters.
        Dictionary<string, object> inParams = new Dictionary<string, object>();
        inParams.Add("SourceClientResourceID", referenceComputerResourceId);
        inParams.Add("RestoreClientResourceID", destinationComputerResourceId);

        // Create the computer association.
       connection.ExecuteMethod("SMS_StateMigration", "AddAssociation", inParams);
    }
    catch (SmsException e)
    {
        Console.WriteLine("failed to make the association" + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `referenceComputerResourceID` | - Managed: `Integer`  <br>- VBScript: `Integer` | The Configuration Manager resource identifier for the reference computer. This is available from `SMS_R_System` class `ResourceId` property for the computer. |
| `destinationComputerResourceID` | - Managed: `Integer`  <br>- VBScript: `Integer` | The Configuration Manager resource identifier for the destination computer. This is available from `SMS_R_System` class `ResourceId` property for the computer. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

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

[About OS deployment computer management](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-computer-management) [AddAssociation Method in Class SMS\_StateMigration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/addassociation-method-in-class-sms_statemigration) [DeleteAssociation Method in Class SMS\_StateMigration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/deleteassociation-method-in-class-sms_statemigration)
