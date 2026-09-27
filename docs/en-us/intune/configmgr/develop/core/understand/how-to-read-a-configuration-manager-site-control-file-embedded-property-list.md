<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-a-configuration-manager-site-control-file-embedded-property-list -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Read a Configuration Manager Site Control File Embedded Property List

In Configuration Manager, you read an embedded property list from a site control file resource by getting the [SMS\_EmbeddedPropertyList](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class) object for the embedded object from the resources *PropLists* property array.

An embedded property list has the following properties that you can set. For more information, see [SMS\_EmbeddedPropertyList](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_embeddedpropertylist-server-wmi-class).

| Value | Description |
| --- | --- |
| PropertyListName | The embedded property name. |
| Values | An array of string values. Each array item represents a single property list item. |

Caution

Making changes to the site control file can cause irreparable damage to your Configuration Manager site.

### To read a site control file embedded property list

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Using the connection object from step one, get a site control file resource. For more information, see [About the Configuration Manager Site Control File](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file).
3. Get the `SMS_EmbeddedPropertyList` for the required embedded property list.
4. Access the property list values by using the `SMS_EmbeddedPropertyList` object *Values* property array.

## Example

The following example method populates the supplied `values` parameter with the *Values* array of the embedded property list `SMS_EmbeddedPropertyList` identified by the `propertyListName` parameter. `true` is returned if the embedded property list is found; otherwise, `false` is returned.

To view code that calls these functions, see [How to Read and Write to the Configuration Manager Site Control File by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-managed-code) or see [How to Read and Write to the Configuration Manager Site Control File by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-wmi).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs

Function GetScfEmbeddedPropertyList(resource,  _
        propertyListName,               _
        ByRef values)

    Dim scfPropertyList

    If IsNull(resource.PropLists) = True Then
        GetScfPropertyList = False
        Exit Function
    End If

    For each scfPropertyList in resource.PropLists
       if   scfPropertyList.PropertyListName = propertyListName Then
            ' Found property list, so return the values array.
            values = scfPropertyList.Values
            GetScfEmbeddedPropertyList = True
            Exit Function
        End If
     Next

     ' Did not find the property list.
     GetScfEmbeddedPropertyList = False
End Function
```

```c#
public bool GetScfEmbeddedPropertyList(
    IResultObject resource,
    string propertyListName,
    out ArrayList values)
{
    values = new ArrayList();
    try
    {
        if (resource.EmbeddedPropertyLists.ContainsKey(propertyListName))
        {
            values.AddRange(resource.EmbeddedPropertyLists[propertyListName]["Values"].StringArrayValue);
            return true;
        }
    }
    catch(SmsException e)
    {
        Console.WriteLine("Couldn't get the embedded property list: " + e.Message);
    }
    return false;

}
```

The sample method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Resource` | - Managed: `IResultObject`  <br>- VBScript: [SWbemObject](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemobject) | The site control file resource that contains the embedded property. |
| `propertyListName` | - Managed: `String`  <br>- VBScript: `String` | The embedded property list to be read. |
| `Values` | - Managed: `String` array  <br>- VBScript: `String` array | The `SMS_EmbeddedProperty` class Values property. An array of string values. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

System.Collections

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

[About the Configuration Manager Site Control File](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-the-configuration-manager-site-control-file) [How to Read and Write to the Configuration Manager Site Control File by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-managed-code) [How to Read and Write to the Configuration Manager Site Control File by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-read-and-write-to-the-site-control-file-by-using-wmi)
