<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-category-to-a-windows-driver -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Add a Category to a Windows Driver

In Configuration Manager, you add a category to a Windows driver by adding the unique identifier for the category to the [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class)`CategoryInstance_UniqueIDs` array property. The array contains one or more string identifiers that match the [SMS\_CategoryInstance Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class)`CategoryInstance_UniqueID` property value. There is an instance of [SMS\_CategoryInstance Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class) object for each category in the system.

Note

The unique identifier for a driver category is prepended with the text "DriverCategories". Other category types have different text.

A category has localization information, and it is from the [SMS\_CategoryInstance Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class)`LocalizedCategoryInstanceName` property that the display name of the category is obtained.

### To add a category to a Windows driver

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get the [SMS\_Driver](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object for the driver you want to add a category to.
3. Get the category name identifier from the [SMS\_CategoryInstance Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class) object that matches the desired category.
4. Add the category identifier to the [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object `CategoryInstance_UniqueIDs` array property.
5. Commit the [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) changes.

## Example

The following example method adds a category to a Windows driver. `driverID` is a valid [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class) object. For more information, see [About Operating System Deployment Driver Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-driver-management).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub AddDriverCategory(connection,driver,categoryName)

    Dim categories
    Dim category
    Dim driverCategoryID
    Dim categoryID
    Dim results
    Dim existingCategory

    ' Find the category that matches the supplied category name.
    Set results = _
      connection.ExecQuery("SELECT * From SMS_CategoryInstance WHERE LocalizedCategoryInstanceName = '" _
      + categoryName+ "'")

    ' If the category was found, add it to the driver.
    For Each category in results

        If IsNull(driver.CategoryInstance_UniqueIDs) or UBound (driver.CategoryInstance_UniqueIDs) = -1 Then
            ' It is empty. Add the category.
            driver.CategoryInstance_UniqueIDs =  Array(category.CategoryInstance_UniqueID)
         Else

            ' Determine if the category is already applied to the driver.
            For each existingCategory in driver.CategoryInstance_UniqueIDs
                if existingCategory = category.CategoryInstance_UniqueID Then
                    WScript.Echo "Already added"
                    Exit Sub
                End If
            Next

            ' Add the category.
            categories = driver.CategoryInstance_UniqueIDs
            Redim Preserve categories (UBound (driver.CategoryInstance_UniqueIDs)+1)
            categories (Ubound (categories)) =  category.CategoryInstance_UniqueID
            driver.CategoryInstance_UniqueIDs = categories
        End If

        driver.Put_
    Next
End Sub
```

```c#
public void AddDriverCategory(
    WqlConnectionManager connection,
    IResultObject driver,
    string categoryName)
{
    try
    {
        // Get the category.
        IResultObject results = connection.QueryProcessor.ExecuteQuery(
        "SELECT * From SMS_CategoryInstance WHERE LocalizedCategoryInstanceName = '" + categoryName + "'");

       ArrayList driverCategories = new ArrayList(driver["CategoryInstance_UniqueIDs"].StringArrayValue);//;driverCategories);

        foreach (IResultObject category in results)
        {
            foreach (string driverCategory in driverCategories)
            {
                // Do nothing if the driver already has the category.
                if (driverCategory == category["CategoryInstance_UniqueID"].StringValue)
                {
                    Console.WriteLine("Already exists");
                    return;
                }
           }

            // Add the category to the action.
           driverCategories.Add(category["CategoryInstance_UniqueID"].StringValue);
        }

        // Update the driver.
        driver["CategoryInstance_UniqueIDs"].StringArrayValue = (string[])driverCategories.ToArray(typeof(string));
        driver.Put();

    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to add the category" + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices-get) | A valid connection to the SMS Provider. |
| `driver` | - Managed: `IResultObject`  <br>- VBScript: `SWbemObject` | The Windows driver. It is an instance of [SMS\_Driver Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_driver-server-wmi-class). |
| `categoryName` | - Managed: `String`  <br>- VBScript: `String` | The name of an existing category. This matches the [SMS\_CategoryInstance Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_categoryinstance-server-wmi-class) `LocalizedCategoryInstanceName` property. |

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

[About Operating System Deployment Driver Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-driver-management) [How to Remove a Category from a Windows Driver](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-remove-a-category-from-a-windows-driver)
