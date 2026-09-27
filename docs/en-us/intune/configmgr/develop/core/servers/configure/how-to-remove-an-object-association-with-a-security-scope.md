<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-remove-an-object-association-with-a-security-scope -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Remove an Object Association with a Security Scope

Removing a security scope from an object instance is as simple as deleting the Windows Management Instrumentation \(WMI\)`SMS_SecuredCategoryMembership` class instance. However, object instances must have at least one security scope associated with them. The last object instance can never be removed. Every object is created with the `Default` security scope, and if all other security scopes are to be removed from an object instance, the `Default` should be added to it before removal.

Important

You must have administrative rights to the scope and the object you are removing it from. If you do not have the correct permissions, removing a scope from that object instance will fail. Removing the last scope from an object will be unsuccessful and will fail.

Tip

To remove multiple objects to a scope, use the [RemoveMemberships Method in Class SMS\_SecuredCategoryMembership](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/removememberships-method-in-class-sms_securedcategorymembership).

### To remove a security scope from an object

1. Set up a connection to the SMS Provider.
2. Determine the object's key property identifier.
3. Determine the object type identifier.
4. Determine the scope identifier.
5. Find an instance of the `SMS_SecuredCategoryMembership` WMI class that matches the .
6. Delete the instance.

## Example

The following code example removes a scope identifier from a package:

```vbs
Sub RemoveObjectScope(connection, scopeId, objectKey, objectTypeId)

    Dim assignment

    ' Find the existing scope assignement that matches our parameters.
    Set assignment = connection.Get("SMS_SecuredCategoryMembership.CategoryID='" & scopeId & "',ObjectKey='" & objectKey & "',ObjectTypeId=" & objectTypeId)

    If (assignment Is Nothing) Then
        Err.Raise 1, "RemoveObjectScope", "Unable to find matching scope, object, and object type."
    Else
        assignment.Delete_
    End If
End Sub
```

```c#
public void RemoveObjectScope(WqlConnectionManager connection, string scopeId, string objectKey, int objectTypeId)
{
    // Find the existing scope assignement that matches our parameters.
     IResultObject assignment = connection.GetInstance("SMS_SecuredCategoryMembership.CategoryID='" + scopeId + "',ObjectKey='" + objectKey + "',ObjectTypeID=" + objectTypeId.ToString());

   // Make sure we found the scope.
    if (assignment == null)
        throw new System.Exception("Unable to find matching scope, object, and object type.");
    else
        assignment.Delete();
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `scopeId` | `String` | The identifier of the security scope. |
| objectKey | `String` | The key property value of the object. |
| objectTypeId | `Integer` | The type identifier of the object referenced in the `objectKey` parameter. |

## Compiling the Code

The C# example requires:

### Namespaces

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## See Also

[SMS\_SecuredCategoryMembership Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_securedcategorymembership-server-wmi-class) [How to Create a New Security Scope](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-create-a-new-security-scope) [How to Delete a Security Scope](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-delete-a-security-scope) [How to Associate an Object with a Security Scope](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-associate-an-object-with-a-security-scope) [SMS\_SecuredCategory Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_securedcategory-server-wmi-class)
