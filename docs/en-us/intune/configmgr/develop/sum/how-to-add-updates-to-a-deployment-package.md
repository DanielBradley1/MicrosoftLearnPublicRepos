<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-add-updates-to-a-deployment-package -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Add Updates to a Deployment Package

You add updates to a software updates deployment package, in Configuration Manager, by obtaining an instance of the [SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatespackage-server-wmi-class) class and by using the [AddUpdateContent](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage) method.

### To create a software updates deployment package

1. Set up a connection to the SMS Provider.
2. Obtain an existing package object by using the `SMS_SoftwareUpdatesPackage` class.
3. Add update content to the existing package using the `AddUpdateContent` method.

## Example

The following example method shows how to add updates to a software updates deployment package by using the `SMS_SoftwareUpdatesPackage` class and the `AddUpdateContent` method.

Note

The updates must be available in the content source path \(as part of the dictionary object `addUpdateContentParameters` in C#\). If the updates exist in a package source, that package source cannot be used for more than one deployment package.

Important

No VBScript example was included, as the `AddUpdateContent` method does not return from the method call on failure. This is a known issue and is being investigated.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

Example of the method call in C#:

```csharp
// PREWORK FOR AddUpdatesToSUMDeploymentPackage

// Define the array of Content Ids to load into addUpdateContentParameters.
int[] newArrayContentIds = new int[] { 82 };

// Define the array of source paths (these must be UNC) to load into addUpdateContentParameters.
string[] newArrayContentSourcePath = new string[] { "\\\\ServerOne\\source1" };

// Load the update content parameters into an object to pass to the method.
Dictionary<string, object> addUpdateContentParameters = new Dictionary<string, object>();
addUpdateContentParameters.Add("ContentIds", newArrayContentIds);
addUpdateContentParameters.Add("ContentSourcePath", newArrayContentSourcePath);
addUpdateContentParameters.Add("bRefreshDPs", false);

AddUpdatestoSUMDeploymentPackage(WMIConnection,
                                 "ABC00001",
                                 addUpdateContentParameters);
```

```csharp
public void AddUpdatestoSUMDeploymentPackage(WqlConnectionManager connection,
                                            string existingSUMPackageID,
                                            Dictionary<string, object> addUpdateContentParameters)
{
    try
    {
        // Get the specific SUM Deployment Package to change.
        IResultObject existingSUMDeploymentPackage = connection.GetInstance(@"SMS_SoftwareUpdatesPackage.PackageID='" + existingSUMPackageID + "'");

        // Add updates to the existing SUM Deployment Package using the AddUpdateContent method.
        // Note: The method will throw an exception, if the method is not able to add the content.
        existingSUMDeploymentPackage.ExecuteMethod("AddUpdateContent", addUpdateContentParameters);

        // Output a success message that the content was added.
        Console.WriteLine("Added content to the SUM deployment package. ");
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to add content to the SUM deployment package.");
        Console.WriteLine("Error: " + ex.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `existingSUMPackageID` | - Managed: `String` | The package ID for an existing software updates deployment package. |
| `addUpdateContentParameters` | - Managed: `dictionary` object | The set of parameters \(`ContentIDs`, `ContentSourcePath`, `bRefreshDPs`\) that is passed into the method and used with the `AddUpdateContent` method call. |

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

## See Also

[About software update deployments](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-software-updates-deployments) [How to Assign a Package to a Distribution Point](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/how-to-assign-a-package-to-a-distribution-point) [SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdatespackage-server-wmi-class) [AddUpdateContent Method in Class SMS\_SoftwareUpdatesPackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage)
