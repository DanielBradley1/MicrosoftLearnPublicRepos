<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-clear-a-pxe-advertisement-for-a-configuration-manager-collection -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Clear a PXE Advertisement For a Configuration Manager Collection

To clear a PXE advertisement for a Configuration Manager collection, you call the [ClearLastNBSAdvForCollection Method in Class SMS\_Collection](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/clearlastnbsadvforcollection-method-in-class-sms_collection) method.

Clearing a PXE advertisement forces the PXE server to re-evaluate the mandatory advertisement that a PXE device must execute on the next PXE boot. It is most often used when the last advertisement that was executed failed or when the advertisement must be re-run. For information about clearing the PXE advertisement for a resource, see [How to Clear a PXE Advertisement for a Configuration Manager Resource](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-clear-a-pxe-advertisement-for-a-configuration-manager-resource).

### To clear a PXE advertisement for a collection

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get the [SMS\_Collection](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) object for the collection you want to clear the PXE advertisement for.
3. Call the `ClearLastNBSAdvForCollection` method to clear the PXE advertisement for the collection.

## Example

The following example clears the PXE advertisement for the collection that is identified by the `collectionID` parameter.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub ClearPxeAdvertisementCollection (connection, collectionID)

    On Error Resume Next
    Dim collection

    ' Get the collection.
    Set collection = connection.Get("SMS_Collection.CollectionID='" & collectionID & "'")

    result = collection.ClearLastNBSAdvForCollection

    if Err.number <> 0 Then
        WScript.Echo "Failed to clear PXE advertisement for collection: " & collectionID
        Exit Sub
    End If

End Sub
```

```c#
public void ClearPxeAdvertisementCollection(WqlConnectionManager connection, string collectionID)
{
    try
    {
        // Get the collection.
        IResultObject collection = connection.GetInstance(@"SMS_Collection.CollectionID='" + collectionID + "'");

        Dictionary<string, object> inParams = new Dictionary<string, object>();
        IResultObject outParams = collection.ExecuteMethod("ClearLastNBSAdvForCollection", inParams);

        if (outParams == null || outParams["StatusCode"].IntegerValue != 0)
        {
            Console.WriteLine
                ("Failed to clear PXE advertisement for collection " + collection["Name"].ToString());
            return;
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to clear PXE advertisement " + e.Message);
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `collectionID` | - Managed: `String`  <br>- VBScript: `String` | The resource identifier. You can obtain this from the `SMS_Collection` class CollectionID property. |

## Compiling the Code

The C# example has the following compilation requirements:

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

[How to Clear a PXE Advertisement for a Configuration Manager Resource](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-clear-a-pxe-advertisement-for-a-configuration-manager-resource) [About image management](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-image-management)
