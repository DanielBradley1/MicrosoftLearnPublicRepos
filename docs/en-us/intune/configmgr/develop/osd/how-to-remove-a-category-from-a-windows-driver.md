<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-remove-a-category-from-a-windows-driver -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Remove a Category from a Windows Driver

In Configuration Manager, you remove a category from a Windows driver by removing the unique identifier for the category from the [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) `CategoryInstance_UniqueIDs` array property.

### To remove a category from a Windows driver

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get the [SMS\_Driver](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object for the driver that you want remove the category from.
3. Get the category name identifier from the [SMS\_CategoryInstance Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class) object that matches the desired category.
4. Remove the category identifier from the [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object `CategoryInstance_UniqueIDs` array property.
5. Commit the [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) changes.

## Example

The following example method removes a category from a Windows driver. `driverID` is a valid [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object. For more information, see [About Operating System Deployment Driver Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-driver-management).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub RemoveDriverCategory(connection,driver,categoryName)

    Dim results
    Dim driverCategoryID
    Dim category
    Dim categories
    Dim i

    If IsNull(driver.CategoryInstance_UniqueIDs) _
           or UBound (driver.CategoryInstance_UniqueIDs) = -1 Then
        ' There are no categories, so quit.
        Wscript.Echo "No categories found"
        Exit Sub
    End If

     Set results = _
      connection.ExecQuery("SELECT * From SMS_CategoryInstance WHERE LocalizedCategoryInstanceName = '" _
      + categoryName+ "'")

    ' If the category was found, delete, if it is there, from the driver.
    For Each category In results

        ' Destination for copied categories.
        categories = Array(driver.CategoryInstance_UniqueIDs)
        i=0

        For Each driverCategoryID in driver.CategoryInstance_UniqueIDs
            If driverCategoryID = category.CategoryInstance_UniqueID Then
                ' Found it, so skip it.
                 Redim Preserve categories (UBound(categories))
            Else
                ' Copy the category.
                categories(i) = driverCategoryID
                i=i+1
            End If
        Next

        ' Make sure the array is empty.
        if i = 0  Then
            Redim categories(-1)
        End If

         driver.CategoryInstance_UniqueIDs = categories
         driver.Put_
    Next
End Sub
```

```c#
public void RemoveDriverCategory(WqlConnectionManager connection,
    IResultObject driver,
    string categoryName)
{
    try
    {
        // Get the category.
        IResultObject results =
            connection.QueryProcessor.ExecuteQuery(
            "SELECT * From SMS_CategoryInstance WHERE LocalizedCategoryInstanceName = '"
            + categoryName
            + "'");

        ArrayList driverCategories = new ArrayList(driver["CategoryInstance_UniqueIDs"].StringArrayValue);

        // Remove the category from the driver.
        foreach (IResultObject category in results)
        {
            driverCategories.Remove(category["CategoryInstance_UniqueID"].StringValue);
        }

        // Update the driver.
        driver["CategoryInstance_UniqueIDs"].StringArrayValue = (string[])driverCategories.ToArray(typeof(string));
        driver.Put();
    }
    catch(SmsException e)
    {
        Console.WriteLine("Failed to remove category :" + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed:`WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `driver` | - Managed: `IResultObject`  <br>- VBScript: `SWbemObject` | The Windows driver. It is an instance of [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class). |
| `categoryName` | - Managed: `String`  <br>- VBScript: `String` | The name of an existing category. This matches the [SMS\_CategoryInstance Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class)e `LocalizedCategoryInstanceName` property. |

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

[About Operating System Deployment Driver Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-driver-management) [How to Add a Category to a Windows Driver](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-category-to-a-windows-driver)
