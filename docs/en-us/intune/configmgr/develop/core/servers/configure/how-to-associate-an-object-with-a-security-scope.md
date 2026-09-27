<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-associate-an-object-with-a-security-scope -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Associate an Object with a Security Scope

Tip

To assign multiple objects to a scope, use the [AddMemberships Method in Class SMS\_SecuredCategoryMembership](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/addmemberships-method-in-class-sms_securedcategorymembership).

### To assign an object a security scope

1. Set up a connection to the SMS Provider.
2. Determine the object's key property identifier.
3. Determine the object type identifier.
4. Create a new instance of the `SMS_SecuredCategoryMembership` WMI class, setting the scope identifier, object key, and object type values.
5. Save the `SMS_SecuredCategoryMembership` object instance.

## Example

The following code example assigns a scope identifier to a package:

```vbs
Sub AddObjectScope(connection, scopeId, objectKey, objectTypeId)

    Dim assignment

    ' Create a new instance of the scope assignment.
    Set assignment = connection.Get("SMS_SecuredCategoryMembership").SpawnInstance_()

    ' Configure the assignment
    assignment.CategoryID = scopeId
    assignment.ObjectKey = objectKey
    assignment.ObjectTypeID = objectTypeId

    ' Commit the assignment
    assignment.Put_

End Sub
```

```c#
public void AddObjectScope(WqlConnectionManager connection, string scopeId, string objectKey, int objectTypeId)
{
    // Create a new instance of the scope assignment.
    IResultObject assignment = connection.CreateInstance("SMS_SecuredCategoryMembership");

    // Configure the assignment
    assignment.Properties["CategoryID"].StringValue = scopeId;
    assignment.Properties["ObjectKey"].StringValue = objectKey;
    assignment.Properties["ObjectTypeID"].IntegerValue = objectTypeId;

    // Commit the assignment
    assignment.Put();
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `scopeId` | `String` | The identifier of the security scope. |
| objectKey | `String` | The key property value of the object to assign a scope to. |
| objectTypeId | `Integer` | The type identifier of the object referenced in the `objectKey` parameter. |

## Compiling the Code

The C# example requires:

### Namespaces

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## See Also

[SMS\_SecuredCategoryMembership Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_securedcategorymembership-server-wmi-class) [How to Create a New Security Scope](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-new-security-scope) [How to Delete a Security Scope](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-delete-a-security-scope) [How to Remove an Object Association with a Security Scope](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-remove-an-object-association-with-a-security-scope) [SMS\_SecuredCategory Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_securedcategory-server-wmi-class)
